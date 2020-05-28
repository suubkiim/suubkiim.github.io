---
title: "About Bazel"
date: 2020-01-06
categories: Build tools
---

## **바젤 개념**

바젤(Bazel)은 소프트웨어 빌드 및 테스트 자동화를 가능하게하는 오픈 소스 도구이다. 

Make , Apache Ant 또는 Apache Maven 과 같은 빌드 도구와 유사하게 Bazel은 일련의 규칙을 사용하여 소스 코드 에서 응용 소프트웨어를 빌드한다 . 규칙과 매크로 는 파이썬(Python) 의 하위 집합 인 Skylark 언어로 작성된다. Java , C , C ++ , Python , Objective-C 및 Bourne 셸 스크립트 프로그래밍 언어로 작성된 소프트웨어 작성을위한 기본 규칙이 있다. Bazel은 Android 및 iOS 운영 체제 용 배포에 적합한 응용 소프트웨어 패키지를 생성할 수 있다.

Bazel을 설계 할 때 빌드 속도, 정확성 및 재현성에 중점을 두었다. 이 도구는 병렬화를 사용하여 빌드 프로세스의 일부분을 가속화한다. 복잡한 빌드 그래프에서 빌드 의존성을 분석하는 데 사용할 수있는 Bazel Query 언어가 포함되어 있다.

 
* 코드 양이 아주 방대하거나 여러가지 언어를 컴파일해야 하는 프로젝트, 다양한 플랫폼을 설치해야 하는 프로젝트 등에서 바젤이 유용하다. 

[ 바젤 알아보기 ] : https://limelab.tistory.com/20

* cf. 안드로이드의 gradle [ 참고 사이트 ] :  https://mullue.github.io/tools/2018/01/07/bazel-Cpp-build.html

* **WORKSPACE File** - 워크스페이스의 디렉토리와 내부파일을 정의한다. 프로젝트 디렉토리 구조에서 루트에 위치

* **BUILD file** - 하나 또는 여러개 파일 존재. 프로젝트의 각 부분을 어떻게 필드할지 정의한다. (빌드파일을 가지는 폴더는 하나의 패키지가 된다.)


## **BUILD File**

BUILD File은 몇가지 지시유형을 내부에 포함한다. 그 첫번째는 Build rule 이며 결과를 얻기 위한 빌드방법을 정의한다.

빌드파일에서의 빌드룰의 인스턴스를 Target이라고 부른다. Target은 소스셋과 종속관계, 또는 다른 Target을 지정한다.

```
#빌드파일 사례
cc_binary(
    name = "hello-world",
    srcs = ["hello-world.cc"],
)
```

여기서 cc_binary가 빌드룰이며, 종속관계가 없는 hello-world.cc 라는 소스파일을 이용하여 실행파일을 빌드하는 룰을 정의하고 있다. name 은 필수속성이다.


## **타겟 라벨링**
Bazel에서 타겟을 라벨링하는 문법은 아래와 같다. (예: `//main:hello-world` or `//lib:hello-time`)

```
//path/to/package:target-name
```
룰 타겟일 경우, path/to/package는 BUILD파일이 저장된 디렉토리경로이고 target-name은 빌드파일에 name 속성을 이용하여 정의한 target이름이다.

파일 타겟일 경우, path/to/package 는 패키지 루트의 경로이고 target-name 은 타겟파일의 이름(전체경로를 포함한)이다.

동일한 패키지내에서는 패키지 경로를 제외하고 //:target-name 로 접근할 수 있다.

동일한 빌드파일 내에서는 //를 제외하고 :target-name 만으로 접근할 수 있다.

 

## **프로젝트 빌드**

(1) 터미널에서 w4/experimental/subinkim/hello_world 로 이동

(2) 명령어 실행 : Admins-MacBook-Pro:hello_world subinkim$ bazel build //hello_world:hello_world

```
$ bazel build //main:hello-world

#여기서 //main: 은 빌드파일의 위치(workspace 루트로부터 상대경로)를 나타내고 
#hello-world는 빌드파일내에 정의된 target의 이름이다.
experimental/subinkim/안에 hello_world라는 파일과 WORKSPACE 파일 생성, 이 안에 hello_world.py와 BUILD파일이 있음. 
```
> 여기에서 WORKSPACE 파일을 따로 만들어 사용했으나, 평소에는 w4 폴더 내에 있는 WORKSPACE 폴더 이용하면 됨 (w4로부터의 상대경로 이용)

(3) 실행 결과

<img src="https://github.com/suubkiim/suubkiim.github.io/blob/master/_images/7e210d5e-1912-48ff-a53b-5ec0acc025a5.png" width=50%>


(4) 빌드 성공

<img src="https://github.com/suubkiim/suubkiim.github.io/blob/master/_images/f92f2286-88f7-4811-ae9c-2ba366acd439.png" width=50%>

cf. 위의 내용과 같이 빌드가 성공적으로 되었을 경우, bazel-bin 디렉토리에 빌드 결과물이 위치하게 됩니다. 아래의 명령어로 바이너리를 실행할 수 있습니다. (https://hiseon.me/c/bazel-tutorial/)

→ (3)번을 보았을 때, bazel-bin/hello_world/hello_world에 빌드 결과물이 위치했음을 알 수 있음

 

(5) Testing

```
#예시
$ bazel-bin/main/hello-world
```

* 실행 결과

<img src="https://github.com/suubkiim/suubkiim.github.io/blob/master/_images/7667d600-429e-44fa-8740-131b69a82b56.png" width=50%>
