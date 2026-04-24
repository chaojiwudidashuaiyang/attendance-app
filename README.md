# attendance-appimport streamlit as st

st.title("📊 出勤率计算器")

total_lessons = 0
total_attend = 0

if "total_lessons" not in st.session_state:
    st.session_state.total_lessons = 0
    st.session_state.total_attend = 0

data = st.text_input("输入（已上课,出席）例如：3,2")

if st.button("计算"):
    try:
        a, b = map(int, data.split(","))
        
        rate = b / a * 100
        
        st.write(f"本课程出勤率：{rate:.1f}%")
        
        st.session_state.total_lessons += a
        st.session_state.total_attend += b
        
        total_rate = st.session_state.total_attend / st.session_state.total_lessons * 100
        
        st.write(f"总出勤率：{total_rate:.1f}%")
        
    except:
        st.error("输入格式错误，请用 3,2")
