# **MCP(Model Context Protocol) 보고서**

## **1\. MCP(Model Context Protocol) 개요**

MCP(Model Context Protocol)는 인공지능(AI) 모델이 외부 데이터 소스, 도구 및 환경과 연결되는 방식을 표준화하기 위해 Anthropic에서 2024년 후반에 처음 공개한 오픈 스탠다드입니다.1 이는 마치 다양한 기기를 하나의 표준 인터페이스로 연결하는 USB-C 포트와 유사하게 AI 애플리케이션을 위한 범용 연결 방식을 제공합니다.1 Anthropic은 AI 어시스턴트가 콘텐츠 저장소, 비즈니스 도구, 개발 환경 등 실제 데이터가 있는 시스템에 연결될 수 있도록 MCP를 개발했으며 3, 오픈 소스 프로토콜로 공개하여 업계 전반의 폭넓은 채택을 장려하고 있습니다.1

최근 대규모 언어 모델(LLM)은 신뢰할 수 있고 개인화된 유용한 출력을 제공하기 위해 고객 데이터에 대한 접근이 필수적입니다.3 그러나 가장 정교한 모델조차 데이터로부터 고립되어 정보 사일로 및 레거시 시스템에 갇혀 있는 경우가 많습니다.12 AI 어시스턴트가 점차 주류로 채택됨에 따라 모델의 추론 능력과 품질은 빠르게 향상되었지만, 여전히 필요한 데이터에 대한 접근은 제한적인 상황입니다.12 이전에는 새로운 데이터 소스마다 고유한 맞춤형 통합이 필요했기 때문에 연결된 시스템을 확장하는 데 어려움이 있었으며 12, 각 API 또는 데이터베이스마다 별도의 사용자 정의 코드를 작성해야 했습니다.2 이러한 기존 방식은 M개의 AI 애플리케이션과 N개의 도구/시스템 간에 M×N개의 개별 통합을 요구하여 복잡성을 증가시켰습니다.4 MCP는 이러한 문제점을 해결하고 AI 모델과 외부 세계 간의 연결을 표준화하기 위해 등장했습니다.

## **2\. MCP의 목적 및 중요성**

MCP의 주요 목적은 AI 모델이 콘텐츠 저장소, 비즈니스 도구, 개발 환경 등 다양한 데이터가 존재하는 시스템에 접근할 수 있도록 하는 것입니다.3 이는 정보 사일로 및 레거시 시스템에 갇혀 있던 AI 모델의 제약을 극복하고 12, 조직 내의 다양한 데이터에 대한 접근성을 향상시켜 AI의 활용 가치를 극대화하는 데 기여합니다. MCP는 단일 프로토콜을 통해 다양한 데이터 소스 및 도구와의 통합을 간소화하여 개발 과정을 효율적으로 만듭니다.2 기존의 M개의 AI 애플리케이션과 N개의 도구/시스템 간의 복잡한 통합 문제를 M+N의 관계로 줄여 개발 및 유지 관리의 부담을 크게 덜어줍니다.4

뿐만 아니라, MCP는 AI 모델이 필요한 데이터에 접근할 수 있도록 지원함으로써 더욱 관련성 높고 정확한 응답을 생성하는 데 도움을 줍니다.12 실시간 데이터에 연결하여 모델의 답변이 최신 정보, 풍부한 컨텍스트, 그리고 특정 도메인에 특화된 내용을 포함하도록 보장합니다.2 또한, MCP는 안전한 양방향 연결을 제공하며 12, 표준화된 인증, 사용 정책 및 데이터 형식을 처리하는 프로토콜을 통해 데이터 접근 및 상호 작용의 보안성을 높입니다.2 더 나아가, MCP는 재사용 가능한 커넥터("서버")의 생태계를 조성하여 개발자가 한 번 개발한 통합을 여러 LLM 및 클라이언트에서 재사용할 수 있도록 지원하며 2, 동일한 통합을 반복해서 개발해야 하는 불필요한 작업을 줄여줍니다.

## **3\. MCP의 주요 이점**

MCP는 다양한 이점을 제공하여 AI 애플리케이션 개발 및 활용 방식을 혁신합니다. 첫째, MCP를 사용하면 새로운 기능을 처음부터 코딩할 필요 없이 기존의 MCP 서버를 통해 빠르고 간편하게 통합할 수 있습니다.2 Google Drive나 SQL 데이터베이스를 위한 MCP 서버가 이미 존재한다면, MCP를 지원하는 모든 AI 앱은 해당 서버에 연결하여 즉시 기능을 활용할 수 있습니다.2 이는 마치 다양한 기능을 갖춘 플러그인을 간편하게 연결하여 사용하는 것과 유사합니다.

둘째, MCP는 AI 에이전트가 내장된 지식에만 의존하는 것이 아니라, 능동적으로 정보를 검색하거나 여러 단계로 이루어진 워크플로우를 자율적으로 수행할 수 있도록 지원합니다.2 예를 들어, 고객 관계 관리(CRM) 시스템에서 데이터를 가져오고, 이메일 발송 도구를 통해 이메일을 보내며, 데이터베이스에 관련 기록을 업데이트하는 일련의 작업을 하나의 흐름으로 자동화할 수 있습니다.2

셋째, MCP는 다양한 서비스와의 통합 과정을 표준화하여 개발 과정에서 발생하는 마찰을 줄이고 설정 과정을 간소화합니다.2 애플리케이션이 MCP를 지원하기만 하면, 단일 메커니즘을 통해 여러 서비스에 연결할 수 있어 2, 새로운 API를 사용할 때마다 복잡한 설정을 반복해야 하는 번거로움을 덜어줍니다.

넷째, MCP는 도구 전반에 걸쳐 일관된 요청 및 응답 형식을 강제합니다.2 따라서 AI 앱은 서비스마다 다른 데이터 형식(예: 서비스 A는 HTTP 응답, 서비스 B는 XML)을 처리할 필요가 없어집니다.2 모델의 출력(함수 호출)과 도구의 결과는 모두 통일된 JSON 구조로 전달되어 디버깅과 확장을 용이하게 하고, 다양한 모델 벤더와의 호환성을 유지하여 상호 운용성을 높입니다.

다섯째, MCP는 단순한 API 호출을 넘어 모델과 도구 간의 지속적인 대화와 컨텍스트 유지를 지원합니다.2 MCP 서버는 도구뿐만 아니라 특정 작업을 위한 사전 정의된 프롬프트 템플릿인 프롬프트와 문서와 같은 데이터 컨텍스트인 리소스를 제공할 수 있습니다.2 이를 통해 AI는 단순히 API를 호출하는 것 외에도 참조 데이터를 활용하거나 서버가 안내하는 복잡한 워크플로우를 따를 수 있습니다.

여섯째, MCP는 AI 모델이 데이터베이스 및 API를 실시간으로 쿼리할 수 있도록 하여 항상 최신 정보에 접근할 수 있도록 합니다.17 사전 캐시된 데이터나 인덱싱된 데이터 세트에 의존하는 대신, 필요할 때마다 최신 데이터를 검색하여 부정확하거나 오래된 응답의 위험을 줄입니다.17

일곱째, MCP는 컨텍스트가 저장, 공유 및 업데이트되는 방식에 대한 표준화된 거버넌스를 제공하여 보안 및 규정 준수를 강화합니다.3 또한, 중간 데이터를 저장하지 않고 필요할 때만 데이터를 가져옴으로써 데이터 유출 및 규정 준수 위험을 줄입니다.17

마지막으로, MCP를 사용하면 개발자는 모든 외부 시스템에 대해 별도의 API 커넥터를 유지 관리할 필요가 없어 개발 속도를 높이고 유지 관리 부담을 줄일 수 있습니다.37 API 업데이트나 변경으로 인해 통합이 중단될 위험을 줄여 개발 팀이 보다 효율적으로 작업하고 AI 애플리케이션의 안정성을 높이는 데 기여합니다.37

## **4\. MCP 아키텍처**

MCP는 클라이언트-서버 아키텍처를 기반으로 합니다.2 여기서 호스트는 Claude Desktop이나 IDE와 같은 LLM 애플리케이션으로, 연결을 시작하고 여러 서버에 연결할 수 있습니다.4 호스트 내에는 클라이언트가 존재하며, 이는 각 서버와 1:1 연결을 유지하면서 서버의 기능 검색, 요청 전달 및 응답 처리를 담당합니다.2 서버는 외부 프로그램으로, 특정 기능(도구, 데이터 접근, 프롬프트)을 제공하며, 다양한 데이터 소스에 연결됩니다.2 서버는 도구, 리소스, 프롬프트를 클라이언트에 제공하여 LLM의 기능을 확장합니다.2

클라이언트와 서버 간의 통신은 JSON-RPC 2.0을 기반으로 이루어집니다.2 JSON-RPC는 경량의 상태 비저장 프로토콜로, AI 워크플로우에서 빠르고 동적인 정보 교환에 적합합니다.21 MCP는 STDIO (Standard Input/Output) 및 HTTP with SSE (Server-Sent Events)를 포함한 다양한 전송 방식을 지원하여 4, 로컬 통신에는 STDIO가, 원격 통신 및 서버에서 클라이언트로의 실시간 업데이트에는 SSE가 주로 사용됩니다.2

## **5\. MCP의 기술적 세부 사항**

MCP 통신은 계층화된 구조를 가지며, 프로토콜 레이어는 메시지 프레이밍, 요청/응답 연결 등 높은 수준의 통신 패턴을 정의합니다.8 전송 레이어는 클라이언트와 서버 간의 실제 통신을 담당하며, JSON-RPC 메시지의 직렬화 및 역직렬화를 처리합니다.26 MCP에서 사용되는 주요 메시지 유형으로는 요청 (Request), 결과 (Result), 오류 (Error), 알림 (Notification) 등이 있습니다.2

MCP 연결은 초기화, 메시지 교환, 종료의 세 단계를 거칩니다.8 초기화 단계에서 클라이언트와 서버는 프로토콜 버전과 지원하는 기능을 서로 협상합니다.2 메시지 교환 단계에서는 요청-응답 패턴과 알림 패턴을 사용하여 실제 통신이 이루어집니다.2 연결 종료는 정상적인 종료, 전송 연결 끊김, 또는 오류 발생과 같은 상황에서 발생할 수 있습니다.8

MCP는 보안을 중요한 고려 사항으로 다루며, 원격 연결 시 TLS 사용, 연결 원점 검증, 필요한 경우 인증 구현 등을 통해 전송 보안을 강화합니다.26 또한, 모든 수신 메시지에 대한 유효성 검사, 입력 삭제, 메시지 크기 제한 확인, JSON-RPC 형식 검증 등을 통해 메시지 무결성을 보장합니다.26 리소스 보호를 위해 액세스 제어 구현, 리소스 경로 검증, 리소스 사용량 모니터링, 요청 속도 제한 등의 메커니즘을 제공합니다.26

MCP 기반 시스템의 안정성을 유지하고 문제를 신속하게 해결하기 위해 프로토콜 이벤트 로깅, 메시지 흐름 추적, 성능 모니터링, 오류 기록 등의 디버깅 및 모니터링 기능이 지원됩니다.26 상태 점검, 연결 상태 모니터링, 리소스 사용량 추적, 성능 프로파일링 등의 진단 기능과 다양한 전송 방식 테스트, 오류 처리 검증, 에지 케이스 확인, 서버 부하 테스트 등의 테스트 기능도 제공됩니다.26

## **6\. MCP의 주요 구성 요소**

MCP는 LLM의 기능을 확장하고 외부 시스템과의 상호 작용을 가능하게 하는 여러 주요 구성 요소로 이루어져 있습니다.

\*\*도구 (Tools)\*\*는 LLM이 특정 작업을 수행하기 위해 호출할 수 있는 실행 가능한 함수입니다.2 예를 들어, 날씨 API를 호출하여 현재 날씨 정보를 얻거나, 데이터베이스를 쿼리하여 특정 정보를 검색하거나, 파일 시스템과 상호 작용하여 파일을 읽고 쓰는 등의 작업을 수행할 수 있습니다.2

\*\*리소스 (Resources)\*\*는 LLM에게 추가적인 컨텍스트 정보를 제공하는 읽기 전용 데이터 소스입니다.2 이는 REST API의 GET 엔드포인트와 유사하며, 문서, 데이터베이스 항목, 파일 등의 형태로 제공될 수 있습니다.2

\*\*프롬프트 (Prompts)\*\*는 특정 작업에 LLM을 효과적으로 활용하기 위해 미리 정의된 템플릿입니다.2 이는 특정 작업을 위한 재사용 가능한 프롬프트 템플릿 및 워크플로우를 생성하는 데 사용됩니다.6

\*\*샘플링 (Sampling)\*\*은 MCP 서버가 클라이언트에게 LLM 완성(Completion)을 요청할 수 있는 기능으로 4, 클라이언트가 모델 선택, 호스팅, 개인 정보 보호 및 비용 관리에 대한 완전한 제어를 유지하면서 서버가 지능형 기능에 액세스해야 하는 시나리오에서 유용합니다.4

마지막으로, \*\*도구 주석 (Tool Annotations)\*\*은 도구에 대한 추가적인 메타데이터를 제공하여 클라이언트가 도구를 더 잘 이해하고 사용자 인터페이스에 적절하게 표시하는 데 도움을 줍니다.32 예를 들어, 도구의 제목, 읽기 전용 여부, 파괴적인 업데이트 가능성 여부, 멱등성 여부 등을 나타낼 수 있습니다.32

## **7\. MCP 워크플로우**

MCP 워크플로우는 클라이언트와 서버 간의 연결 설정으로 시작됩니다. 호스트 애플리케이션은 MCP 클라이언트를 초기화하고 서버와의 연결을 설정합니다.2 이 과정에서 클라이언트는 초기화 메시지를 보내 프로토콜 버전 및 기능을 서버와 핸드셰이크합니다.2 연결이 설정되면 클라이언트는 서버가 제공하는 기능, 즉 도구, 리소스, 프롬프트를 검색합니다.2 일반적으로 tools/list 요청을 통해 사용 가능한 도구 목록과 그 설명을 얻을 수 있습니다.2

사용자가 외부 작업이 필요한 질문을 하면 LLM은 어떤 특정 도구를 사용해야 할지 결정합니다.2 이 결정은 프롬프트 엔지니어링이나 LLM의 함수 호출 능력을 통해 이루어질 수 있습니다.2 도구가 선택되면 클라이언트는 선택된 도구의 이름과 필요한 매개변수를 포함하여 tools/call 요청을 서버에 보냅니다.2 서버는 이 요청을 받아 해당 도구의 기본적인 로직을 실행하고, 그 결과를 JSON 형식으로 클라이언트에게 반환합니다.2 마지막으로, MCP 클라이언트는 서버로부터 받은 도구의 실행 결과를 호스트 애플리케이션의 AI 응답에 통합하여 사용자에게 최종 답변을 제공합니다.2 이 과정에서 결과를 대화에 다시 삽입하고 모델에게 계속 응답하도록 요청하는 방식이 흔히 사용됩니다.2

## **8\. JSON-RPC 기반 통신**

MCP는 클라이언트와 서버 간의 통신을 위해 JSON-RPC 2.0 메시지 형식을 사용합니다. JSON-RPC 메시지는 jsonrpc, id, method, params 필드를 포함하는 JSON 객체로 구성됩니다.2 jsonrpc 필드는 JSON-RPC 프로토콜의 버전을 나타내고, id 필드는 요청을 식별하는 데 사용됩니다. method 필드는 호출할 메서드 이름을 지정하며, params 필드는 메서드 호출에 필요한 매개변수를 포함합니다. 성공적인 응답 메시지는 result 필드에 결과를 담고, 오류가 발생한 경우에는 error 필드에 오류 정보를 담습니다.2 응답을 기대하지 않는 일방향 메시지인 알림 메시지는 id 필드를 포함하지 않습니다.2

다음은 각 메시지 유형의 예시입니다.

* **요청**: {"jsonrpc": "2.0", "id": 1, "method": "tools/list", "params": {}} 2  
* **응답**: {"jsonrpc": "2.0", "id": 1, "result": \[{"name": "get\_weather", "description": "...", "parameters": {...}}\], "error": null} (예시)  
* **오류**: {"jsonrpc": "2.0", "id": 1, "result": null, "error": {"code": \-32602, "message": "Invalid params"}} 49  
* **알림**: {"jsonrpc": "2.0", "method": "notifications/tools/list\_changed", "params": {}} (예시)

이러한 표준화된 메시지 형식을 통해 MCP는 클라이언트와 서버 간의 효율적이고 안정적인 통신을 지원하며, 다양한 시스템 간의 상호 운용성을 높이는 데 중요한 역할을 합니다.

## **9\. 전송 방식 (STDIO, SSE)**

MCP는 클라이언트와 서버 간의 통신을 위해 두 가지 주요 전송 방식을 제공합니다.

**STDIO (Standard Input/Output)** 전송 방식은 클라이언트가 MCP 서버를 별도의 하위 프로세스로 실행하고, 운영체제의 표준 입력 및 출력을 통해 JSON-RPC 메시지를 주고받는 방식입니다.4 이 방식은 클라이언트와 서버가 동일한 머신에서 실행되는 로컬 통합 및 명령줄 도구 개발에 특히 유용하며 4, 각 클라이언트-서버 연결은 1:1 관계를 가집니다.14 STDIO는 로컬 환경에서 간단하고 효율적인 통신을 제공하지만, 원격 환경에서는 보안상의 고려가 필요할 수 있습니다.

**SSE (Server-Sent Events)** 전송 방식은 HTTP 프로토콜을 기반으로 서버에서 클라이언트로 스트리밍 방식으로 데이터를 전송하는 방식입니다.2 클라이언트는 서버로 HTTP POST 요청을 보내고, 서버는 SSE를 통해 실시간으로 메시지를 클라이언트에게 전송합니다. 이 방식은 원격 통신 및 서버에서 클라이언트로의 실시간 업데이트가 필요한 경우에 적합하며 2, DNS 리바인딩 공격에 취약할 수 있으므로 보안에 특별히 유의해야 합니다.45

각 전송 방식은 고유한 장단점을 가지며, 사용 사례에 따라 적합한 방식을 선택해야 합니다. STDIO는 구현이 간단하고 로컬 통신에 효율적이지만, 원격 통신에는 적합하지 않고 보안 위험이 있을 수 있습니다. 반면, SSE는 서버에서 클라이언트로의 실시간 스트리밍이 가능하고 HTTP 호환성이 높지만, DNS 리바인딩 공격에 취약할 수 있으며 일부 클라이언트만 지원할 수 있습니다.24 따라서 전송 방식 선택은 사용 환경 및 요구 사항을 신중하게 고려하여 이루어져야 합니다. 향후에는 HTTP 기반의 스트리밍 방식이 더 널리 사용될 것으로 예상됩니다.47

## **10\. 도구, 리소스, 프롬프트**

MCP는 LLM의 기능을 확장하고 외부 시스템과의 상호 작용을 용이하게 하는 세 가지 주요 구성 요소인 도구, 리소스, 프롬프트를 제공합니다.

\*\*도구 (Tools)\*\*는 LLM이 외부 시스템과 상호 작용하여 특정 작업을 수행할 수 있도록 하는 실행 가능한 기능입니다. 이는 "최신 주가 가져오기", "이메일 보내기", "데이터베이스 업데이트" 등 다양한 형태로 구현될 수 있습니다.2

\*\*리소스 (Resources)\*\*는 LLM에게 컨텍스트 정보를 제공하는 읽기 전용 데이터입니다. 이는 "회사 위키 문서", "최근 보고서", "사용자 프로필 정보" 등 다양한 형태의 데이터를 포함할 수 있습니다.2

\*\*프롬프트 (Prompts)\*\*는 특정 작업에 LLM을 효과적으로 활용하기 위한 사전 정의된 템플릿으로, "이메일 초안 작성", "코드 리뷰 요청", "회의 요약 생성" 등 다양한 작업에 맞게 설계될 수 있습니다.2

이러한 도구, 리소스, 프롬프트 외에도 MCP는 \*\*도구 주석 (Tool Annotations)\*\*을 제공합니다. 이는 도구에 대한 추가적인 메타데이터를 제공하여 클라이언트가 도구를 더 잘 이해하고 사용자 인터페이스에 적절하게 표시하는 데 도움을 줍니다.32 예를 들어, 도구의 제목, 읽기 전용 여부, 파괴적인 업데이트 가능성 여부, 멱등성 여부 등을 나타낼 수 있습니다.32

## **11\. 클라이언트-서버 모델**

MCP는 클라이언트-서버 모델을 기반으로 하며, 호스트, 클라이언트, 서버 세 가지 주요 구성 요소가 상호 작용합니다. 호스트는 사용자 인터페이스를 제공하고 클라이언트를 관리하며 LLM과의 상호 작용을 조율하는 역할을 합니다.4 클라이언트는 호스트 내에서 실행되며 서버와의 연결을 관리하고 메시지를 중개하는 역할을 수행합니다.2 서버는 외부 시스템에 연결하여 도구, 리소스, 프롬프트를 제공하는 역할을 합니다.2 이 세 가지 주요 컴포넌트 간의 긴밀한 협력을 통해 MCP는 AI 모델이 외부 세계와 효과적으로 소통하고 상호 작용할 수 있도록 지원합니다.

MCP 생태계에는 이미 다양한 클라이언트와 서버가 존재합니다. **MCP 클라이언트**의 예로는 Claude Desktop, Cursor, Windsurf, Microsoft Copilot Studio, LibreChat, Claude Code, Zed, Cline, Firebase Genkit, LangGraph, OpenAI agents sdk, Emacs Mcp, Apify MCP Tester, mcp-agent, Smithery.ai 등이 있습니다.2 **MCP 서버**의 예로는 GitHub, Slack, Google Drive, Git, Postgres, Puppeteer, Brave Search, Docker, SingleStore, DuckDuckGo Search, Cloudflare, Vectorize, Neo4j, Home Assistant 등이 있습니다.2 이러한 다양한 클라이언트와 서버의 존재는 MCP 생태계가 이미 활발하게 성장하고 있으며, 앞으로 더욱 많은 애플리케이션과 서비스에서 MCP를 지원할 것으로 예상할 수 있다는 점을 시사합니다.

## **12\. 결론**

MCP는 AI 모델이 외부 세계와 상호 작용하는 방식을 혁신할 수 있는 중요한 기술로 부상했습니다.2 다양한 시스템과의 통합을 표준화하고 간소화함으로써 AI 애플리케이션의 개발 및 배포를 용이하게 하며 2, 더욱 강력하고 유연한 AI 솔루션을 가능하게 합니다.2

MCP 생태계는 앞으로도 지속적으로 확장될 것으로 예상되며, 더 많은 클라이언트 및 서버 구현이 등장할 것입니다.2 또한, 보안 및 개인 정보 보호를 강화하기 위한 추가적인 기능 개발도 기대됩니다.2 다양한 산업 분야에서 MCP를 활용한 혁신적인 AI 애플리케이션이 등장할 것으로 전망되며 2, MCP는 아직 초기 단계이지만, AI 생태계의 중요한 인프라로 자리매김하여 앞으로 더욱 강력하고 다양한 기능을 제공할 것으로 기대됩니다.

#### **참고 자료**

1. diamantai.substack.com, 4월 20, 2025에 액세스, [https://diamantai.substack.com/p/model-context-protocol-mcp-explained\#:\~:text=Model%20Context%20Protocol%20(MCP)%20is,C%20port%20for%20AI%20applications.](https://diamantai.substack.com/p/model-context-protocol-mcp-explained#:~:text=Model%20Context%20Protocol%20\(MCP\)%20is,C%20port%20for%20AI%20applications.)  
2. Model Context Protocol (MCP): A comprehensive introduction for developers \- Stytch, 4월 20, 2025에 액세스, [https://stytch.com/blog/model-context-protocol-introduction/](https://stytch.com/blog/model-context-protocol-introduction/)  
3. What you need to know about the Model Context Protocol (MCP), 4월 20, 2025에 액세스, [https://www.merge.dev/blog/model-context-protocol](https://www.merge.dev/blog/model-context-protocol)  
4. MCP 101: An Introduction to Model Context Protocol \- DigitalOcean, 4월 20, 2025에 액세스, [https://www.digitalocean.com/community/tutorials/model-context-protocol](https://www.digitalocean.com/community/tutorials/model-context-protocol)  
5. Model Context Protocol (MCP) \- Anthropic API, 4월 20, 2025에 액세스, [https://docs.anthropic.com/en/docs/agents-and-tools/mcp](https://docs.anthropic.com/en/docs/agents-and-tools/mcp)  
6. Model Context Protocol: Introduction, 4월 20, 2025에 액세스, [https://modelcontextprotocol.io/introduction](https://modelcontextprotocol.io/introduction)  
7. Model Context Protocol (MCP) Clearly Explained : r/LLMDevs \- Reddit, 4월 20, 2025에 액세스, [https://www.reddit.com/r/LLMDevs/comments/1jbqegg/model\_context\_protocol\_mcp\_clearly\_explained/](https://www.reddit.com/r/LLMDevs/comments/1jbqegg/model_context_protocol_mcp_clearly_explained/)  
8. What is Model Context Protocol (MCP): Explained \- Composio, 4월 20, 2025에 액세스, [https://composio.dev/blog/what-is-model-context-protocol-mcp-explained/](https://composio.dev/blog/what-is-model-context-protocol-mcp-explained/)  
9. Model Context Protocol (MCP) Hands-On Walkthrough for the Unstructured Workflow Endpoint, 4월 20, 2025에 액세스, [https://docs.unstructured.io/examplecode/tools/mcp](https://docs.unstructured.io/examplecode/tools/mcp)  
10. Model Context Protocol (MCP): Integrating Azure OpenAI for Enhanced Tool Integration and Prompting \- Microsoft Tech Community, 4월 20, 2025에 액세스, [https://techcommunity.microsoft.com/blog/azure-ai-services-blog/model-context-protocol-mcp-integrating-azure-openai-for-enhanced-tool-integratio/4393788](https://techcommunity.microsoft.com/blog/azure-ai-services-blog/model-context-protocol-mcp-integrating-azure-openai-for-enhanced-tool-integratio/4393788)  
11. Model Context Protocol (MCP): 8 MCP Servers Every Developer Should Try\!, 4월 20, 2025에 액세스, [https://dev.to/pavanbelagatti/model-context-protocol-mcp-8-mcp-servers-every-developer-should-try-5hm2](https://dev.to/pavanbelagatti/model-context-protocol-mcp-8-mcp-servers-every-developer-should-try-5hm2)  
12. Introducing the Model Context Protocol \- Anthropic, 4월 20, 2025에 액세스, [https://www.anthropic.com/news/model-context-protocol](https://www.anthropic.com/news/model-context-protocol)  
13. What is the Model Context Protocol (MCP)? — WorkOS, 4월 20, 2025에 액세스, [https://workos.com/blog/model-context-protocol](https://workos.com/blog/model-context-protocol)  
14. Model Context Protocol (MCP) an overview \- Philschmid, 4월 20, 2025에 액세스, [https://www.philschmid.de/mcp-introduction](https://www.philschmid.de/mcp-introduction)  
15. Why Your Company Should Know About Model Context Protocol \- Nasuni, 4월 20, 2025에 액세스, [https://www.nasuni.com/blog/why-your-company-should-know-about-model-context-protocol/](https://www.nasuni.com/blog/why-your-company-should-know-about-model-context-protocol/)  
16. Anthropic's Model Context Protocol (MCP) is way bigger than most people think : r/ClaudeAI, 4월 20, 2025에 액세스, [https://www.reddit.com/r/ClaudeAI/comments/1gzv8b9/anthropics\_model\_context\_protocol\_mcp\_is\_way/](https://www.reddit.com/r/ClaudeAI/comments/1gzv8b9/anthropics_model_context_protocol_mcp_is_way/)  
17. The Future of Connected AI: What is an MCP Server and Why It ..., 4월 20, 2025에 액세스, [https://www.hiberus.com/en/blog/the-future-of-connected-ai-what-is-an-mcp-server/](https://www.hiberus.com/en/blog/the-future-of-connected-ai-what-is-an-mcp-server/)  
18. Model Context Protocol (MCP): A Guide With Demo Project \- DataCamp, 4월 20, 2025에 액세스, [https://www.datacamp.com/tutorial/mcp-model-context-protocol](https://www.datacamp.com/tutorial/mcp-model-context-protocol)  
19. A beginners Guide on Model Context Protocol (MCP) \- OpenCV, 4월 20, 2025에 액세스, [https://opencv.org/blog/model-context-protocol/](https://opencv.org/blog/model-context-protocol/)  
20. Model Context Protocol Integration — AgentIQ \- NVIDIA Docs, 4월 20, 2025에 액세스, [https://docs.nvidia.com/agentiq/latest/components/mcp.html](https://docs.nvidia.com/agentiq/latest/components/mcp.html)  
21. What is the Model Context Protocol (MCP)? A Complete Guide \- Treblle Blog, 4월 20, 2025에 액세스, [https://blog.treblle.com/model-context-protocol-guide/](https://blog.treblle.com/model-context-protocol-guide/)  
22. Model Context Protocol explained as simply as possible \- Sean goedecke, 4월 20, 2025에 액세스, [https://www.seangoedecke.com/model-context-protocol/](https://www.seangoedecke.com/model-context-protocol/)  
23. Model Context Protocol (MCP) Quickstart \- Glama, 4월 20, 2025에 액세스, [https://glama.ai/blog/2024-11-25-model-context-protocol-quickstart](https://glama.ai/blog/2024-11-25-model-context-protocol-quickstart)  
24. Model Context Protocol \- Cursor, 4월 20, 2025에 액세스, [https://docs.cursor.com/context/model-context-protocol](https://docs.cursor.com/context/model-context-protocol)  
25. Specification \- Model Context Protocol, 4월 20, 2025에 액세스, [https://modelcontextprotocol.io/specification/2025-03-26](https://modelcontextprotocol.io/specification/2025-03-26)  
26. Core architecture \- Model Context Protocol, 4월 20, 2025에 액세스, [https://modelcontextprotocol.io/docs/concepts/architecture](https://modelcontextprotocol.io/docs/concepts/architecture)  
27. What is Model Context Protocol? \- Portkey, 4월 20, 2025에 액세스, [https://portkey.ai/blog/model-context-protocol-for-llm-appls](https://portkey.ai/blog/model-context-protocol-for-llm-appls)  
28. model-context-protocol-resources/guides/mcp-server-development-guide.md at main \- GitHub, 4월 20, 2025에 액세스, [https://github.com/cyanheads/model-context-protocol-resources/blob/main/guides/mcp-server-development-guide.md](https://github.com/cyanheads/model-context-protocol-resources/blob/main/guides/mcp-server-development-guide.md)  
29. model-context-protocol-resources/guides/mcp-client-development-guide.md at main, 4월 20, 2025에 액세스, [https://github.com/cyanheads/model-context-protocol-resources/blob/main/guides/mcp-client-development-guide.md](https://github.com/cyanheads/model-context-protocol-resources/blob/main/guides/mcp-client-development-guide.md)  
30. Transports \- Model Context Protocol Specification, 4월 20, 2025에 액세스, [https://spec.modelcontextprotocol.io/specification/2024-11-05/basic/transports/](https://spec.modelcontextprotocol.io/specification/2024-11-05/basic/transports/)  
31. Prompts \- Model Context Protocol, 4월 20, 2025에 액세스, [https://modelcontextprotocol.io/docs/concepts/prompts](https://modelcontextprotocol.io/docs/concepts/prompts)  
32. Tools \- Model Context Protocol, 4월 20, 2025에 액세스, [https://modelcontextprotocol.io/docs/concepts/tools](https://modelcontextprotocol.io/docs/concepts/tools)  
33. Model Context Protocol Server \- Home Assistant, 4월 20, 2025에 액세스, [https://www.home-assistant.io/integrations/mcp\_server/](https://www.home-assistant.io/integrations/mcp_server/)  
34. Model Context Protocol (MCP) :: Spring AI Reference, 4월 20, 2025에 액세스, [https://docs.spring.io/spring-ai/reference/api/mcp/mcp-overview.html](https://docs.spring.io/spring-ai/reference/api/mcp/mcp-overview.html)  
35. Model Context Protocol (MCP) \- PydanticAI, 4월 20, 2025에 액세스, [https://ai.pydantic.dev/mcp/](https://ai.pydantic.dev/mcp/)  
36. Example Clients \- Model Context Protocol, 4월 20, 2025에 액세스, [https://modelcontextprotocol.io/clients](https://modelcontextprotocol.io/clients)  
37. Benefits of using MCP over traditional integration methods \- Portkey, 4월 20, 2025에 액세스, [https://portkey.ai/blog/benefits-of-mcp-over-traditional-integration/](https://portkey.ai/blog/benefits-of-mcp-over-traditional-integration/)  
38. What is MCP (Model Context Protocol) and how it works \- Logto blog, 4월 20, 2025에 액세스, [https://blog.logto.io/what-is-mcp](https://blog.logto.io/what-is-mcp)  
39. Can someone explain MCP to me? How are you using it? And what has it allowed you to do that you couldn't do before? : r/ClaudeAI \- Reddit, 4월 20, 2025에 액세스, [https://www.reddit.com/r/ClaudeAI/comments/1h55zxd/can\_someone\_explain\_mcp\_to\_me\_how\_are\_you\_using/](https://www.reddit.com/r/ClaudeAI/comments/1h55zxd/can_someone_explain_mcp_to_me_how_are_you_using/)  
40. The Comprehensive Guide to Model Context Protocol (MCP) \- tl;dv, 4월 20, 2025에 액세스, [https://tldv.io/blog/model-context-protocol/](https://tldv.io/blog/model-context-protocol/)  
41. How to Use Model Context Protocol the Right Way | Boomi, 4월 20, 2025에 액세스, [https://boomi.com/blog/model-context-protocol-how-to-use/](https://boomi.com/blog/model-context-protocol-how-to-use/)  
42. What is Model Context Protocol (MCP)? How it simplifies AI integrations compared to APIs | AI Agents That Work \- Norah Sakal, 4월 20, 2025에 액세스, [https://norahsakal.com/blog/mcp-vs-api-model-context-protocol-explained/](https://norahsakal.com/blog/mcp-vs-api-model-context-protocol-explained/)  
43. Everything a Developer Needs to Know About the Model Context Protocol (MCP) \- Neo4j, 4월 20, 2025에 액세스, [https://neo4j.com/blog/developer/model-context-protocol/](https://neo4j.com/blog/developer/model-context-protocol/)  
44. Introducing Model Context Protocol (MCP) in Copilot Studio: Simplified Integration with AI Apps and Agents \- Microsoft, 4월 20, 2025에 액세스, [https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/introducing-model-context-protocol-mcp-in-copilot-studio-simplified-integration-with-ai-apps-and-agents/](https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/introducing-model-context-protocol-mcp-in-copilot-studio-simplified-integration-with-ai-apps-and-agents/)  
45. Transports \- Model Context Protocol, 4월 20, 2025에 액세스, [https://modelcontextprotocol.io/docs/concepts/transports](https://modelcontextprotocol.io/docs/concepts/transports)  
46. Which MCP Server Transport is Better? Comparing STDIO and SSE : r/modelcontextprotocol, 4월 20, 2025에 액세스, [https://www.reddit.com/r/modelcontextprotocol/comments/1k0doby/which\_mcp\_server\_transport\_is\_better\_comparing/](https://www.reddit.com/r/modelcontextprotocol/comments/1k0doby/which_mcp_server_transport_is_better_comparing/)  
47. MCP Servers will support HTTP on top of SSE/STDIO but not websocket \- Reddit, 4월 20, 2025에 액세스, [https://www.reddit.com/r/modelcontextprotocol/comments/1jhhokc/mcp\_servers\_will\_support\_http\_on\_top\_of\_ssestdio/](https://www.reddit.com/r/modelcontextprotocol/comments/1jhhokc/mcp_servers_will_support_http_on_top_of_ssestdio/)  
48. stdio vs SSE transport question \#63 \- GitHub, 4월 20, 2025에 액세스, [https://github.com/modelcontextprotocol/specification/discussions/63](https://github.com/modelcontextprotocol/specification/discussions/63)  
49. How is JSON-RPC used in the Model Context Protocol? \- Milvus, 4월 20, 2025에 액세스, [https://milvus.io/ai-quick-reference/how-is-jsonrpc-used-in-the-model-context-protocol](https://milvus.io/ai-quick-reference/how-is-jsonrpc-used-in-the-model-context-protocol)  
50. What is MCP? Model Context Protocol Explained \- Workato, 4월 20, 2025에 액세스, [https://www.workato.com/the-connector/what-is-mcp/](https://www.workato.com/the-connector/what-is-mcp/)  
51. Benefits of Implementing the Making Care Primary (MCP) Model \- Acclivity Health, 4월 20, 2025에 액세스, [https://acclivityhealth.com/benefits-of-implementing-the-making-care-primary-mcp-model/](https://acclivityhealth.com/benefits-of-implementing-the-making-care-primary-mcp-model/)