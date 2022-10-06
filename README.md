# htmlJspProject1
[join.html]
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>This is htmljsp project assignment 4 that I'm taking in a bootcamp</title>
</head>
<body>

<form action="join" method="post">

<table border width="400">
<tr>
<td colspan=2 bgcolor="#A3A3A3"><b>Step1 : 아이디/비번 입력</b></td>
</tr>
<tr>
<td>아이디: </td>
<td><input type="text" name="id"></td>
</tr>
<tr>
<td>비밀번호: </td>
<td><input type="password" name="pwd"></td>
</tr>
<tr>
<td>비밀번호 확인: </td>
<td><input type="password" name="pwdCf"></td>
</tr>

<tr><td colspan=2 bgcolor="#A3A3A3"><b>Step2 : 개인정보</b></td></tr>
<tr><td>성별: </td><td><input type="radio" name="gender" value="남성">남자
<input type="radio" name="gender" value="여성">여자</td></tr>
<tr><td>혈액형: </td>
<td><select name="blood" >
<option value="A형">A형
<option> B형
<option> AB형
<option> O형
</select>
</td></tr>
<tr><td>생일:</td> <td><input type="date" name="birth"></td></tr>

<tr><td colspan=2 bgcolor="#A3A3A3"><b>Step3 : 선호도</b></td></tr>
<tr><td>취미:</td><td><input type="checkbox" name="hobby" value="축구">축구
<input type="checkbox" name="hobby" value="야구">야구
<input type="checkbox" name="hobby" value="농구">농구
</td></tr>
<tr><td>좋아하는 색깔 </td><td><input type="color" name="color"></td></tr>

<tr><td colspan=2 bgcolor="#A3A3A3"><b>Step4 : 하고 싶은 말</b></td></tr>
<tr><td colspan=2><textarea name = "memo" rows="3" cols="50"></textarea></td></tr>

</table>

<input type="submit" value="제출">
<input type="reset" value="초기화"><br>
</form>

</body>
</html>


[Join.java]

protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
request.setCharacterEncoding("UTF-8");
response.setContentType("text/html;charset=utf-8");
PrintWriter out = response.getWriter();

String id = request.getParameter("id");
String pwd = request.getParameter("pwd");
String cf = request.getParameter("pwdCf");
String gender = request.getParameter("gender");
String blood = request.getParameter("blood");
String birth = request.getParameter("birth");
String [] hobby = request.getParameterValues("hobby");
String color = request.getParameter("color");
System.out.print(color);
String memo = request.getParameter("memo");


out.print("<html><head><title>Join</title></head><html>");
out.print("<body>");

out.print("아이디:" + id + "<br>");
out.print("비밀번호: " + pwd + "<br>");
if (!pwd.equals(cf)) out.print("비밀번호가 일치하지 않습니다. <br>" );
out.print("성별: " + gender + "<br>");
out.print("혈액형: "+blood);
out.print("<br>" + "생일: " + birth + "<br>");
out.print("취미: ");
for (String h:hobby) {
out.print(h + " ");
}
out.print("<br>" +"좋아하는 색: <div style='width:100px;height:100px;background:" + color + "'></div>");
out.print("남기고 싶은 말: ");
out.print(memo);

out.print("</body");
out.print("</html>");

}
