# tips


# Multiple SSH keys for different accounts on Github or Gitlab

## referencs
#### https://stackoverflow.com/questions/7927750/specify-an-ssh-key-for-git-push-for-a-given-domain
#### https://coderwall.com/p/7smjkq/multiple-ssh-keys-for-different-accounts-on-github-or-gitlab

	Host gitolite-as-alice
	HostName git.company.com
	User git
	IdentityFile /home/whoever/.ssh/id_rsa.alice
	IdentitiesOnly yes

	Host gitolite-as-bob
	HostName git.company.com
	User git
	IdentityFile /home/whoever/.ssh/id_dsa.bob
	IdentitiesOnly yes


	git remote add alice git@gitolite-as-alice:whatever.git
	git remote add bob git@gitolite-as-bob:whatever.git

