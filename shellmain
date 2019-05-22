#默认参数配置
remotedir=/midware/ipop-admin
remoteips_dev=(10.203.109.135)
remoteips_qa=(10.203.109.159 10.203.109.160)
remoteips_prod_ipop=(10.203.72.74 10.203.72.75)
remoteips_prod_sboard=(10.203.72.76 10.203.72.77)

remotebakfile=bak
remotereadyfile=ready
remoteuser=root

locshell=shell-dev.sh
remoteshell=shell.sh
locshelldir=D:/SGM/IPOP-server/

locfile=IPOP-server-0.0.1-SNAPSHOT.war
remotefile=IPOP-server-0.0.1-SNAPSHOT.war
locfiledir=D:/SGM/IPOP-server/target/

branch=BRANCH_DEV_1.0.0
app=ipop
env=dev


main(){
    while true
    do
	    selectapp
	    cd $locshelldir
	    echo ""
        #echo -e "\e[1;32m  (cd $locshelldir)\e[0m\n"
	    while true
	    do
	        selectenv
            #git checkout $branch
            echo ""
	        while true
	        do
	            selectipToDeploy
	            break
    	    done
    	    echo -en "\n是否还需要部署其他环境?: y/n:"
            read v
            if [ -z $v ]; then
                echo -e "\e[1;32m不部署其他环境\e[0m"
                break
            fi
            if [ $v == "y" ]||[ $v == "1" ]; then
                continue;
            else
                echo -e "\e[1;32m不部署其他环境\e[0m"
            fi
            break
    	done
    echo -en "\n是否还需要部署其他应用?: y/n:"
    read v
    if [ -z $v ]; then
        echo -e "\e[1;32m不部署其他应用\e[0m"
        sleep 0.5
        echo -en "\n................................................................................................\e[1;32mexit"
        sout 1 1
        exit
    fi
	if [ $v == "y" ]||[ $v == "1" ]; then
	    continue;
    else
        echo -e "\e[1;32m不部署其他应用\e[0m"
        sleep 0.5
        echo -en "\n................................................................................................\e[1;32mexit"
        sout 1 1
        exit
	fi
    done
}

sout(){
    i=$1
    while true
    do
        echo -en "\e[1;32m."
        sleep $2
        i=$[i-1];
        if [ $i -lt 0 ]; then
            break
        fi
    done
}

selectipToDeploy(){
    for i in ${remoteips[@]}
    do
        remoteip=$i
    	echo -en "\e[1;32m..................................... 正在部署:$remoteip ....................................\e[0m"
        deploy
    done



}
selectenv(){
    while true
    do
	    echo -n "输入部署环境（1-->dev  2-->qa  3-->prod ）:"
	    read v
	    if [ -z $v ]; then
    	    #locshell=shell-dev.sh
    	    #branch=BRANCH_DEV_1.0.0
    	    env=dev
    	    remoteips=${remoteips_dev[@]}
	        echo -e "\e[1;32m========================================== 部署环境:$env ==========================================\e[0m"
	    else
	        if [ $v == "1" ]; then
	            #locshell=shell-dev.sh
    	        #branch=BRANCH_DEV_1.0.0
    	        env=dev
    	        remoteips=${remoteips_dev[@]}
	            echo -e "\e[1;32m========================================== 部署环境:$env ==========================================\e[0m"
	            break;
	        fi
	        if [ $v == "2" ]; then
    	        #locshell=shell-qa.sh
    	        #branch=BRANCH_QA_1.0.0
    	        env=qa
    	        remoteips=${remoteips_qa[@]}
	            echo -e "\e[1;32m========================================== 部署环境:$env ==========================================\e[0m"
	            break;
	        fi
	        if [ $v == "3" ]; then
	            #locshell=shell-prod.sh
    	        #branch=master
    	        env=prod
    	        remoteips=${remoteips_prod_ipop[@]}
    	        if [ $app == "sboard" ]; then
    	            remoteips=${remoteips_prod_sboard[@]}
    	        fi
	            echo -e "\e[1;32m========================================== 部署环境:$env ==========================================\e[0m"
	            break;
	        fi

	        echo -e "\e[1;31m不要瞎写\e[0m"
	        continue
	    fi
	    break
	done
}
selectapp(){
    while true
    do
	    echo -n "输入部署的应用（1-->ipop  2-->mportal  3-->sform  4-->sboard）:"
	    read v
	    if [ -z $v ]; then
            app=ipop
            locfile=IPOP-server-0.0.1-SNAPSHOT.war
            locfiledir=D:/SGM/IPOP-server/target/
            locshelldir=D:/SGM/IPOP-server/
            remotedir=/midware/ipop-admin
            remotefile=IPOP-server-0.0.1-SNAPSHOT.war
	        echo -e "\e[1;32m########################################## 默认部署应用$app #######################################\e[0m"
	    else
	        case "$v" in
              "1")
                app=ipop
                locfile=IPOP-server-0.0.1-SNAPSHOT.war
                locfiledir=D:/SGM/IPOP-server/target/
                locshelldir=D:/SGM/IPOP-server/
                remotedir=/midware/ipop-admin
                remotefile=IPOP-server-0.0.1-SNAPSHOT.war
    	        echo -e "\e[1;32m########################################## 部署应用$app #########################################\e[0m"
                break
                ;;
              "2")
                app=mportal
                locfiledir=D:/SGM/mPortal-server/target/
                locfile=mportal-server-0.0.1-SNAPSHOT.war
                locshelldir=D:/SGM/mPortal-server/
                remotedir=/midware/ipop-mportal
                remotefile=mportal-server-0.0.1-SNAPSHOT.war
    	        echo -e "\e[1;32m########################################## 部署应用$app #########################################\e[0m"
                break
                ;;
              "3")
                app=sform
                locfiledir=D:/SGM/sForm-server/target/
                locfile=dynamic-form-0.0.1-SNAPSHOT.jar
                locshelldir=D:/SGM/sForm-server/
                remotedir=/midware/ipop-sform
                remotefile=dynamic-form-0.0.1-SNAPSHOT.jar
    	        echo -e "\e[1;32m########################################## 部署应用$app #########################################\e[0m"
                break
                ;;
              "4")
                app=sboard
                locfiledir=D:/SGM/sBoard-server/target/
                locfile=sboard.war
                locshelldir=D:/SGM/sBoard-server/
                remotedir=/midware/apache-tomcat-8.5.28/webapps
                remotefile=ROOT.war
    	        echo -e "\e[1;32m########################################## 部署应用$app #########################################\e[0m"
                break
                ;;
            esac
	        echo -e "\e[1;31m输入错误，请重新选择\e[0m"
	        continue
	    fi
	    break
	    echo ""
	done
}

deploy(){
    echo -en "\n是否全自动部署? y/n:"
	read v
	if [ -z $v ]; then
	    echo -e "\e[1;32m手动部署\e[0m"
	    deployhand
        echo  -e "\e[1;32m..................................... 部署完毕:$remoteip ....................................\e[0m\n"
	    return
	fi
	if [ $v == "y" ]||[ $v == "1" ]; then
		echo  -e "\e[1;32m自动部署\e[0m"
        deployauto
    else
	    echo  -e "\e[1;32m手动部署\e[0m"
        deployhand
	fi

	echo ""
    echo  -e "\e[1;32m..................................... 部署完毕:$remoteip ....................................\e[0m\n"
}

deployauto(){
	git pull
	mvn clean package -Dmaven.test.skip=true

	checkdir $remotedir
	checkdir $remotedir/$remotebakfile
	checkdir $remotedir/$remotereadyfile

	upload $locshelldir $locshell $remoteuser $remoteip $remotedir            $remoteshell
	upload $locfiledir  $locfile  $remoteuser $remoteip $remotedir/$remotereadyfile $remotefile

	shell $remoteuser $remoteip $remotedir $remoteshell bak $env
	shell $remoteuser $remoteip $remotedir $remoteshell stop $env
	shell $remoteuser $remoteip $remotedir $remoteshell update $env
	shell $remoteuser $remoteip $remotedir $remoteshell start $env
}

deployhand(){
	echo -n "是否更新代码? y/n:"
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不更新代码 \e[0m"
	else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        git pull
        else
            echo  -e "\e[1;32m \b不更新代码 \e[0m"
	    fi
	fi

	echo -n "是否打包? y/n:"
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不打包 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
    	    mvn clean package -Dmaven.test.skip=true
        else
            echo  -e "\e[1;32m \b不打包 \e[0m"
	    fi
	fi

	echo -n "是否确认目录? y/n:"
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不确认目录 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        checkdir $remotedir
	        checkdir $remotedir/$remotebakfile
	        checkdir $remotedir/$remotereadyfile
        else
            echo  -e "\e[1;32m \b不确认目录 \e[0m"
	    fi
	fi

	echo -n "是否上传脚本? y/n:"
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不上传脚本 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        upload $locshelldir $locshell $remoteuser $remoteip $remotedir   $remoteshell
        else
            echo  -e "\e[1;32m \b不上传脚本 \e[0m"
	    fi
	fi

	echo -n "是否上传代码包? y/n:"
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不上传代码包 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        upload $locfiledir  $locfile  $remoteuser $remoteip $remotedir/$remotereadyfile $remotefile
        else
            echo  -e "\e[1;32m \b不上传代码包 \e[0m"
	    fi
	fi

	echo -n "是否备份? y/n:"
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不备份 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        shell $remoteuser $remoteip $remotedir $remoteshell bak $env
        else
            echo  -e "\e[1;32m \b不备份 \e[0m"
	    fi
	fi

	echo -n "是否停止服务? y/n: "
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不停止服务 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        shell $remoteuser $remoteip $remotedir $remoteshell stop $env
        else
            echo  -e "\e[1;32m \b不停止服务 \e[0m"
	    fi
	fi

	echo -n "是否更新代码? y/n: "
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不更新代码 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        shell $remoteuser $remoteip $remotedir $remoteshell update $env
        else
            echo  -e "\e[1;32m \b不更新代码 \e[0m"
	    fi
	fi

	echo -n "是否启动服务? y/n: "
	read v
	if [ -z $v ]; then
    echo  -e "\e[1;32m \b不启动服务 \e[0m"
    else
        if [ $v == "y" ]||[ $v == "1" ]; then
	        shell $remoteuser $remoteip $remotedir $remoteshell start $env
        else
            echo  -e "\e[1;32m \b不启动服务 \e[0m"
	    fi
	fi
}

checkdir(){
    ssh $remoteuser@$remoteip "[ -d $1 ] && echo -e \"\e[1;32mdir:$1 is ok \e[0m\" || mkdir -p $1"
}
upload(){
    scp -r $1$2 $3@$4:$5/$6
}
shell(){
    ssh $1@$2 "cd $3/; sh ./$4 $5 $6 > nohup.out"
}



case "$1" in
  "")
    main
    ;;
esac

