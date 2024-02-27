# Align # 
# 1. 웹사이트에서 제공되는 모든 언어의 데이터 수집

- **수집사이트** - '[https://www.tensorflow.org'](https://www.tensorflow.org'/)
- 아래에 해당하는 **20개의 국가의 데이터**를 가져옴
    - language_codes = **'en', 'es-419', 'fr', 'id', 'it', 'pl', 'pt-br', 'vi', 'tr', 'ru', 'he', 'ar', 'fa', 'hi', 'bn', 'th', 'zh-cn', 'zh-tw', 'ja', 'ko’**
- **BeautifulSoup**을 사용하여 크롤링
    1. 초기 작업 - 수집사이트에서 타고 들어갈수 있는 모든 링크 데이터 수집
        1. 나라별 웹사이트 수 24~32개
    2. 추후 작업 - 얼라인(align) 작업을 위하여 다국어로 공통으로 포함된 링크만 남겨둠
        1. 유튜브 제거 및 다국어로 되어 있지 않은 링크 제거
        2. 최종 : 나라별 웹사이트 수 21개
- 링크내에 모든 데이터를 수집하기 위하여 **<p>태그를 기준으로 데이터 수집 진행**
- 최종 데이터 건수 및 구조
    - json 형태 : {국가 : { link : value}}
    - 국가별 - 약 4만~ 6만 문장
    - 총데이터 약 100만 문장

# 2. 수집한 데이터를 문장 기준으로 얼라인(align)하기

- 참고 논문 - https://www.nature.com/articles/s41598-023-47479-w
- 참고 githug - https://github.com/bfsujason/bertalign
- Bertalign을 사용하여 sample로 영어 - 프랑스어 얼라인(align)작업을 진행 하였음
- Bertalign 선정이유 :
    - 해당 논문을 참고하여 Bertalign이 여러 성능 측정 지표에서 다른 align 알고리즘들보다 우수한 성능을 보여 선택
    - 정밀도, 재현율, F1 Score에서도 Bertalign이 가장 높은 성능을 보여줌
