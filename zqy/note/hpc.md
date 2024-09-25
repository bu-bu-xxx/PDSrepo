使用`singularity`指南

[polyu文档参考](https://www.polyu.edu.hk/its/researchsupport/en/hpc-platform/user-guides-videos/#uda)

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

`ssh`登入的是你的实际环境

在`Apptainer`里有`nvidia-smi`，但是没有`singularity`

`ssh`里支持`singularity`，但是没有`nvidia-smi`

所以需要先ssh登入，然后复制`singularity`到家目录，然后设置`export PATH=`，就可以跑`singularity & nvidia-smi`，**这个方法行不通**

# sbatch (support gpu)

使用方法

[参考polyu文档](https://connectpolyu-my.sharepoint.com/personal/itsupres_connect_polyu_hk/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fitsupres%5Fconnect%5Fpolyu%5Fhk%2FDocuments%2FResearchWebPage%2FSHPC%2FOOD%2FSHPC%5Ftensorflow%5Fgpu%5Fsingularity%5Fexample%2Epdf&parent=%2Fpersonal%2Fitsupres%5Fconnect%5Fpolyu%5Fhk%2FDocuments%2FResearchWebPage%2FSHPC%2FOOD&ga=1)

Prepare the job script file. (Filename: ngc_tf_m.sbatch)

```shell
#!/bin/bash
#Test for Tensorflow job running with 1 node, 1 task (1 process) with 
limited with 8 tasks per 1 core
#SBATCH --partition= h07gpuq1 # partition name
#SBATCH --time=04:00:00 # walltime
#SBATCH --nodes=1
#SBATCH --ntasks=1 # number of processor cores (i.e. tasks)
#SBATCH --cpus-per-task=4
#SBATCH --mem-per-cpu=4096M # memory per CPU core
#SBATCH --gres=gpu:1
#SBATCH -J "ngc_tf_m" # job name
module load singularity/3.11.3
srun singularity exec --nv tensorflow_22.04-tf2-py3.sif 
python ./ngc_tf_m.py > result.txt

```

```shell
# submit script
sbatch ngc_tf_m.sbatch

# Enquiry the submitted job status
squeue -l
```



