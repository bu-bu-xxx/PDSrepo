使用`singularity`指南

![image-20240925123455526](./assets/image-20240925123455526.png)

---------------------------

`ssh` 登入`hpc platform`指南，因为用上面的连接，过一段时间无操作，会自动断开

```shell
ssh <netID>@h07.its.polyu.edu.hk
```

# 其他

```shell
[24112456g@h07mgt1 ~]$ whereis singularity
singularity: /hpc/hpcapps/singularity/singularity-ce-3.11.3/bin/singularity
```

用HPC登入vscode，实际上是登入一个container

用ssh方式是直接登入

在`vscode`容器里有`nvidia-smi`，没有权限访问`singularity`

但是在系统环境里支持`singularity`

所以需要先ssh登入，然后复制`singularity`到家目录，然后设置`export PATH=`，就可以跑`singularity & nvidia-smi`



