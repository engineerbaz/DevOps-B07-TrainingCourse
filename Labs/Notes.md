### Bash Completion
`apt install bash-completion`
exit the shell then

type `_init_completion`
If success, then you have bash completion otherwise do

`source /usr/share/bash-completion/bash_completion`

### kubectl completion


`echo 'source <(kubectl completion bash)' >>~/.bashrc`
and `kubectl completion bash >/etc/bash_completion.d/kubectl`

```shell
echo 'alias k=kubectl' >>~/.bashrc
echo 'complete -F __start_kubectl k' >>~/.bashrc
```

Refer : https://kubernetes.io/docs/reference/kubectl/cheatsheet/#kubectl-autocomplete

