# Pandas
Let's learn pandas with public opendata course!

Learn to use pandas, matplotlib, folium, pandas_datareader

handling git is hard.

https://pandas.pydata.org/pandas-docs/stable/index.html  
https://matplotlib.org/  
https://python-visualization.github.io/folium/  
https://pandas-datareader.readthedocs.io/en/latest/index.html  

***

[업무 시 참고하면 좋은 기능]

- **groupby**는 기본임. groupby 기준 열을 여러 개 할 수도 있고, groupby된 df를 **agg**로 추가 계산(이것도 여러 개)이 가능하며, 결과물로 피벗테이블과 같은 표를 만들 수 있음. gpt한테 물어보면 잘 알려줌  
    - df.groupby("기준변수")[('계산변수1','계산변수2')].sum() 이런식으로도 사용했었네  
- merge도 기본임. 방법이 여러가지  
    - 합치려는 df의 변수를 **set_index**로 동하게 인덱싱 후 join 사용  
    -   **merge** 함수도 있음. 이게 좀 더 전통적인 db 다루는 방식과 비슷  
- dataframe 날짜 비교 시, **pd.Timestamp(년,월,일,시,분,초)**로 사용. 해당 클래스에 메소드(날짜, 시간)도 있음.  
- **apply**으로 연산된 새로운 변수 생성 기능 많이 사용  
- row추가하는 기능 많이 사용  
    - **concat**을 사용했었네. concat은 여러개 row를 추가 가능함. 근데 dict타입으로 만들어야 해서 귀찮음. 다른거도 있음..  
    - 
- 파이썬 기본 in 기능과 같은 **isin** 메소드를 dataframe에서 사용 할 수 있다.  
    ex) df["변수이름"].isin([원소1,원소2])  
    - 관련해서 **~**연산자를 dataframe앞에 붙이면 NOT을 의미  
    - 그리고 dataframe를 클래스처럼 사용 가능함. **df.변수이름** 이렇게  
- 비밀번호 걸린 엑셀 파일을 읽는 패키지 **msoffcrypto**  
    ex)  
    import msoffcrypto  
    import io  
    import pandas as pd  
  
    def get_df_from_password_excel(excelpath, password):  
        df = pd.DataFrame()  
        temp = io.BytesIO()  
        with open(excelpath, 'rb') as f:  
            excel = msoffcrypto.OfficeFile(f)  
            excel.load_key(password)  
            excel.decrypt(temp)  
            df = pd.read_excel(temp,dtype=object)  
            del temp  
        return df  
- **isnull** 메소드로 결측값 확인하기  
- df가 가공돼서 변경이 되면 **reset_index** 메소드로 초기화 해주는게 좋음.  
- 파일 읽어올 떄, **dtype=object**로 해야 raw data가 됨..  
- 가끔 **encoding** 맞춰야 하는 경우도 있음  
- **python-dateutil**로 날짜 다루는 방법도 있음  
- 