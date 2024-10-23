# crawling-data
데이터 크롤링
# AutoCrawler
Google, Naver 다중 프로세스 이미지 크롤러(고품질 및 속도 및 사용자 지정 가능)

![](docs/animation.gif)

# 사용법

1. Chrome 설치

2. pip install -r requirements.txt

3. 키워드 찾아쓰기 keywords.txt 안에

4. **실행 "main.py"**

5. 파일이 '다운로드' 디렉토리에 다운로드됩니다.


# Arguments
usage:
```
python3 main.py [--skip true] [--threads 4] [--google true] [--naver true] [--full false] [--face false] [--no_gui auto] [--limit 0]
```

```
--skip true        다운로드한 디렉토리가 이미 있는 경우 키워드 건너뛰기. 이는 다시 다운로드할 때 필요합니다.

--threads 4        다운로드할 스레드 수입니다.

--google true      google.com 에서 다운 (boolean)

--naver true       naver.com 에서 다운 (boolean)

--full false       썸네일 대신 전체 해상도 이미지 다운로드(느림)

--face false       Face 검색 모드

--no_gui auto      GUI mode 없음. 전체_해상도 모드의 경우 가속이 가능하지만 썸네일 모드에서는 불안정합니다.
                   기본값: "자동" - full=false이면 거짓, full=true이면 참
                   
--limit 0          사이트당 다운로드 할 최대 수 (0: 무한대)
--proxy-list ''    쉼표로 구분된 프록시 목록은 다음과 같습니다: "socks://127.0.0.1:1080,http://127.0.0.1:1081".
                   모든 스레드는 목록에서 무작위로 하나를 선택합니다.
```


# Full Resolution Mode

full true를 지정하여 JPG, GIF, PNG 파일의 전체 해상도 이미지를 다운로드할 수 있습니다

![](docs/full.gif)



# 데이터 불균형 감지

파일 수에 따라 데이터 불균형을 감지합니다.

크롤링이 끝나면 메시지에 평균 파일의 50% 미만이 있는 디렉토리가 표시됩니다.

해당 디렉토리를 제거하고 다시 다운로드하는 것이 좋습니다.


# 서버에서 SSH를 통해 원격으로 크롤링

```
sudo apt-get install xvfb <- 이게 가상 디스플레이

sudo apt-get install screen <- 이렇게 하면 실행 중에 SSH 터미널을 닫을 수 있습니다.

screen -S s1

Xvfb :99 -ac & DISPLAY=:99 python3 main.py
```

# 커스터마이징

collect_links.py를 변경하여 나의 크롤러를 만들 수 있습니다

# 문제 해결 방법

Google 사이트가 지속적으로 변경됨에 따라 "'collect_links.py'를 수정해야 할 수도 있습니다

1. Google 이미지로 이동합니다. [https://www.google.com/search?q=dog&source=lnms&tbm=isch ](https://www.google.com/search?q=dog&source=lnms&tbm=isch) )
2. Chrome에서 개발자 도구를 엽니다. (CTRL+SHIFT+I, CMD+OPTION+I)
3. 캡처할 이미지를 지정합니다.
![클린샷 2023-10-24, 175957@2x](https://github.com/YoongiKim/AutoCrawler/assets/38288705/6488d6df-1f01-4dfd-8691-6c0ac142fc04)
4. 확인 collect_links.py
![클린샷 2023-10-24, 1802 35@2x](https://github.com/YoongiKim/AutoCrawler/assets/38288705/097c6c03-dd43-45d4-939e-2f677f595362)
5. XPATH 사용을 위한 문서: [https://www.w3schools.com/xml/xpath_syntax.asp ](https://www.w3schools.com/xml/xpath_syntax.asp) )
6. 크롬 개발자 도구에서 CTRL+F를 사용하여 XPATH를 테스트할 수 있습니다.
![클린샷 2023-10-24, 18 05 14@2x](https://github.com/YoongiKim/AutoCrawler/assets/38288705/7ce2601f-9d53-48ff-a1cf-1a2befcc510f)
7. 크롤링하여 일할 수 있는 논리를 찾아야 합니다.
