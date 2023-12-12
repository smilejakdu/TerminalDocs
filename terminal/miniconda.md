# miniconda 셋팅

miniconda3 를 python 가상환경 셋팅을 위한 셋팅이다.



{% embed url="https://repo.anaconda.com/miniconda/" %}

에서 버전선택이 가능하다.

```bash
brew install wget # wget 을 우선 설치를 해야한다.
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
# miniconda 설치를 해준다.
chmod -R 755 Miniconda3-latest-MacOSX-x86_64.sh 
# Miniconda3 를 설치한다.
# 만약 위에 설치가 되지않는다면 rm -rf 으로 삭제하고 arm 을 설치해보자.
./Miniconda3-latest-MacOSX-x86_64.sh # 으로 설치한다.

```

설치가 끝났으면 가상환경을 만들어주면 된다.

```bash
conda 가상환경 만들기

#파이썬3 버전의 환경만들기 
conda create -n "가상환경이름" python=3.9

#conda activate "가상환경이름"
conda 내가 만든 가상환경으로 활성화하기 

#conda activate "가상환경이름"
만약에 되지 않는다면 , 
source activate "가상환경이름"

#conda 실행된 가상환경 비활성화하기
conda deactivate 


# conda 가상환경 삭제하기
conda env remove -n "가상환경이름" 

```



