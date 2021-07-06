# Context-Analysis-Chatbot_Memory-Network / 맥락 분석 챗봇


> 한국인공지능연구소 1기 / 자연어처리 / AURA 팀</br>
> Korea Artificial Intelligence Laboratory 1st / Natural Language Processing / Team AURA

### 이전 깃허브 계정 <https://github.com/hkim-tech/>에서 옮겨왔습니다. 
<div>
<p>
<strong>현재 서버에 올라와 있는 앱은 학습모델이 적용이 되어있지 않습니다.</strong>
데이터 학습 시간이 오래걸려  heroku boot timeout으로 인하여 Crashed 되었으니 이 점 참고하여 소스를 Clone 받으시고 직접 실행 시켜주시기 바랍니다.
(aurabot보다 aurabot_save에서 server.py를 실행시키는 것이 더 빠릅니다.)
</p>
</div>
<div>
  <p>
<strong>Apps that are currently on the server are not covered by the learning model.</strong> Since the data learning time is long and it has been crashed due to heroku boot timeout, please clone the source and execute it manually. (It is faster to run server.py in aurabot_save folder than aurabot folder.)
  </p>
</div>
<div>
  <p>
<strong>AuraBot is the name of this project chatbot.</strong>
    
- 아우라봇 링크 / AuraBot Link: <https://aurabot.herokuapp.com>
- 발표자료 링크 / Powerpoint(pdf) Link: https://drive.google.com/open?id=1ipDY8ybgZ-iJGok4qqr9AaWIEK4atz_l
- 한국인공지능연구소 1기 AURA 팀 링크 / Lab-Aura Team Link: https://www.ai-lab.kr/labs/aura-raebjang-gimhyeonu
    </p>
  </div>
## Screenshots
![default](https://user-images.githubusercontent.com/41403001/44778524-29e4e900-abb8-11e8-9646-ce516b41419a.JPG)
![1](https://user-images.githubusercontent.com/41403001/44778580-5dc00e80-abb8-11e8-91d9-901fbfccc224.JPG)
![3](https://user-images.githubusercontent.com/41403001/44778623-73cdcf00-abb8-11e8-9ab5-3e9521e98ca1.JPG)
![2](https://user-images.githubusercontent.com/41403001/44778625-75979280-abb8-11e8-869d-4dd423a70c65.JPG)

## Background / 연구 배경
한국인공지능연구소 1기 마지막 발표에서 자연어 처리로 팀원 모두 합심하여 할 수 있는 것을 찾던 중 챗봇을 처음부터 끝까지 만들어 보면 어떨까 하는 생각에서 이번 발표 주제를 챗봇으로 선정하였습니다.

In the final announcement of the 1st Korea Institute of Artificial Intelligence, we decided to make the chatbot from the beginning to the end while looking for a project that all the team members could cooperate in natural language processing.

이번에 연구를 진행한 챗봇은 메모리 네트워크 모델로 구성된 상황인지 기반 챗봇으로 사람이 시나리오를 구성하는 방식이 아니라 무작위 수집한 데이터 내에서 관련 있는 맥락을 찾아 질문에 답하는 방식인 End To End 방식으로 구성되어 있습니다.

The chatbots that have been studied in this study are based on the memory network model, which is a context-based chatbot. It is not based on how a person configures scenarios but consists of an end-to-end method of locating related contexts in randomly collected data and answering questions .

## Technology / 기술 설명
메모리 네트워크는 데이터를 메모리에 저장하여 맥락을 이해하여 질문에 대한 답을 하는 방식으로 사용자의 질문을 이용하여 맥락 정보를 선택하는 스토리 선택 모듈과 선택된 스토리 정보와 질문 정보로 답변을 선택하는 탑변 선택 모듈로 구성되어 있습니다.

A memory network is a way of storing data in memory, understanding the context and answering questions. This chatbot consists of a story selection module that selects context information using the user's question and an answer selection module that selects the answer with selected story information and question information.

이러한 단일 메모리 네트워크가 여러 개로 구성된 형태로 답변을 예측하여 이번 연구에서는 3개의 멀티 레이어 구조의 메모리 네트워크로 연구를 진행되었습니다.

In order to predict responses in the form of multiple single memory networks, this research has been conducted with three multi-layered memory networks.

## Research direction / 연구 방향
2017년 창원 대학교의 메모리 네트워크를 이용한 End-to-End 방식의 레스토랑 예약 시스템에 착안하여 첫 질문은 맥락 없이 답변하고 그 이후 질문은 이전 질 을 맥락정보로 활용하여 답변하도록 데이터 셋을 구성하였습니다.

In 2017, I settled on an end-to-end restaurant reservation system using the memory network of Changwon University. The first question was answered without context, and the subsequent question was composed of data to be answered by using the previous quality as context information.

## Research scope / 연구 범위
본 연구에서는 데이터 구성부터 클라이언트 구현까지 챗봇 구성을 위한 모든 프로세스를 다루며, 맥락을 이해하여 답변하는 End-to-End 챗봇의 Prototype 구현을 목적으로 합니다.

This study covers all processes for configuring chatbot from data configuration to client implementation and aims at implementing prototype of end-to-end chatbot that understands the context and answers.

## Model structure / 모델 구조

- 서버 파트: 서버 파트에서는 메모리 네트워크를 통해 미리 정의된 데이터를 학습하고 준비하고 Bottle을 통해 클라이언트 파트에서 받은 질문에 대한 답변을 제시하는 역할을 합니다.

- Server Part: The server part learns and prepares predefined data through the memory network and provides answers to questions received from the client parts through the bottle.

- 클라이언트 파트: 클라이언트 파트는 사용자의 입력을 받아 서버 파트에 전달하고 서버 파트에서 예측된 답변을 화면에 노출해줍니다. 서버와 클라이언트 간에는 json 기반의 REST 통신으로 데이터를 전달합니다.

- Client Part: The client part receives the user's input, passes it on to the server part, and exposes the expected response from the server part to the screen. It transfers data between server and client through json-based REST communication.

---
본 프로젝트와 관련해 질문이 있으시면 hyunwoo.developer@gmail.com으로 이메일 보내주시면 답장드리겠습니다.

If you have any questions about this project, please email hyunwoo.developer@gmail.com.
