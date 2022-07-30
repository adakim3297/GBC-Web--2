# Command Injection

## low

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/CJ%20low-1.png?raw=true" width="500" height="400"/>

    Window에서 입력했을 시 나올 결과에 대해 코드에서 설명해준다. (Ping)

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/CJ%20low-2.png?raw=true" width="500" height="400"/> 

    Ping을 이용하는 등 주소로 Command Injection 한다.
    
    답 : 127.0.0.1

## Medium

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/CJ%20meduim-1.png?raw=true" width="500" height="400"/> 

    '&&' => '',
    ';' => '', 
    을 통해서 &과 ;을 이용해 Command Injection 할 수 있다.

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/CJ%20medium%20-2.png?raw=true" width="500" height="400"/> 

    답 : 127.0.0.1 &;& dir
    {다양한 답이 있을 수 있다.}

## High

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/CJ%20high-1.png?raw=true" width="500" height="400"/> 

    '| ' => ' ' 에서 |뒤에 간격이 있을 을 알 수 있고, 따라서 간격을 이용해 Command Injection을 할 수 있다.

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/CJ%20high-2.png?raw=true" width="500" height="400"/> 
   답: 127.0.01 || dir

   {다양한 답이 있을 수 있다.}

# File Upload
<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20%EC%97%85%EB%A1%9C%EB%93%9C%20%ED%8C%8C%EC%9D%BC%20%EC%BD%94%EB%93%9C.png?raw=true" width="400" height="300"/> 

    이번 해킹을 하기전에 Php라는 파일을 사용하기 위한 사전 작업, 즉 위의 코드로 파일을 만든다.

    low 단계에서의 파일 이름 : webshell.php

    medium 단계에서의 파일 이름 : whebtool.php

    {파일 코드는 같지만 구분을 하고자 파일이름을 달리 하였다.}

## Low

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20low%20-1.png?raw=true" width="500" height="400"/> 
<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20low%20-2.png?raw=true" width="500" height="400"/> 
    
    post 방식으로 업로드 하는 것과 성공할 경우 hackable/upload/를 보며 해킹 할 수 있다.

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20low%20-3.png?raw=true" width="600" height="500"/> 
<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20low%20-4.png?raw=true" width="700" height="250"/> 
    
    웹에서 터미널처럼 명령어를 입력하며 해킹할 수 있다.

    localhost/dvwa/hackable/uploads/webshell.php?cmd = (       )

    괄호 안에 명령어를 입력하면 cmd 터미널에서 입력하는 것과 같은 효과를 볼 수 있다.

## Medium

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20medium%20-1.png?raw=true" width="500" height="400"/> 

    파일 업로드시 이미지 파일 즉, jpeg 또는 png로 업로드 해야 함을 알려준다.

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20medium%20-2.png?raw=true" width="500" height="400"/> 

    파일 업로드할때 php이므로 업로드가 되지 않은 것이다.

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20medium-3.png?raw=true" width="500" height="400"/> 

    프록시를 이용해 application/octet-stream을 image/png로 명령어를 변경해 파일을 이미지 파일로 바꿔서 업로드하도록 한다.

<img src = "https://github.com/adakim3297/GBC-Web--2/blob/main/FU%20medium%20-4.png?raw=true" width="500" height="400"/> 

    그 결과 webtool.php가 성공적으로 업로드되며 low 단계와 같이 localhost/dvwa/hackable/uploads/webshell.php?cmd = (       )을 이용해 해킹을 한다.

## High

    File Inclusion을 알아야 하므로 pass