---
{"dg-publish":true,"permalink":"/contents/1-life/tips/requirements-txt/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":false,"dgShowLocalGraph":false,"dgShowInlineTitle":false}
---


# requirements.txt

```bash
# 설치된 패키지 리스트 추출
pip freeze > ./requirements.txt

# requirements.txt에 명시된 패키지 버전 pip 이용해서 한번에 설치하기
pip -r ./requirements.txt
```

- 현재 environment에 설치되어 있는 package는 보통 아래와 같이 requirements.txt 파일로 추출하고 필요할 때 한번에 설치하곤 했었는데, 아래 `cffi`나 `cryptograph` 같은 몇몇 패키지들이 ==버전 대신 `@ file`의 형태로 표기가 되는 경우==가 있다. 설치할 때 이 부분에서 에러가 발생해서 수동으로 고쳐주곤 했었는데 해결방법을 찾은거 같다.

```c
...
brotlipy==0.7.0
bs4==0.0.1
certifi==2021.5.30
cffi @ file:///private/var/folders/sy/f16zz6x50xz3113nwtb9bvq00000gp/T/abs_62rp5d8fd4/croots/recipe/cffi_1659598655556/work
charset-normalizer==2.0.2
click==8.0.1
cryptography @ file:///private/var/folders/sy/f16zz6x50xz3113nwtb9bvq00000gp/T/abs_b470f7cb-c8f1-42c9-b84f-23789ea77e7c9difcqh4/croots/recipe/cryptography_1652101134392/work
cssselect==1.1.0
dateparser==1.1.1
debugpy==1.6.3
...
```


```bash
# 이렇게 시도해보자!
pip list --format=freeze > requirements.txt
```

- 아까와 달리 버전이 제대로 표기가 되는 것을 확인할 수 있다. 즉, 설치가 깔끔하게 이루어진다!

```r
...
brotlipy==0.7.0
bs4==0.0.1
certifi==2021.5.30
cffi==1.15.1
charset-normalizer==2.0.2
click==8.0.1
cryptography==37.0.1
cssselect==1.1.0
dateparser==1.1.1
debugpy==1.6.3
...
```


# 참고
[python - pip freeze doesn't show package version - Stack Overflow](https://stackoverflow.com/questions/61765502/pip-freeze-doesnt-show-package-version)