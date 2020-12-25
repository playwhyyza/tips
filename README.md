# tips


# Multiple SSH keys for different accounts on Github or Gitlab

## referencs
#### https://stackoverflow.com/questions/7927750/specify-an-ssh-key-for-git-push-for-a-given-domain
#### https://coderwall.com/p/7smjkq/multiple-ssh-keys-for-different-accounts-on-github-or-gitlab

Even if the user and host are the same, they can still be distinguished in ~/.ssh/config. For example, if your configuration looks like this:

	Host gitolite-as-alice
	HostName git.company.com
	User git
	IdentityFile /home/whoever/.ssh/id_rsa.alice
	IdentitiesOnly yes

	Host gitolite-as-bob
	HostName git.company.com
	User git
	IdentityFile ~/.ssh/id_dsa.bob
	IdentitiesOnly yes

Then you just use gitolite-as-alice and gitolite-as-bob instead of the hostname in your URL:

	git remote add alice git@gitolite-as-alice:whatever.git
	git remote add bob git@gitolite-as-bob:whatever.git

Note

You want to include the option IdentitiesOnly yes to prevent the use of default ids. Otherwise, if you also have id files matching the default names, they will get tried first because unlike other config options (which abide by "first in wins") the IdentityFile option appends to the list of identities to try. See: https://serverfault.com/questions/450796/how-could-i-stop-ssh-offering-a-wrong-key/450807#450807

