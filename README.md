# htmlJspProject1
[join.html]
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>This is htmljsp project assignment 4 that I'm taking in a bootcamp</title>
  <br>
  This code should work in eclipse IDE with tomcat v9.0
</head>
  
<body>

<form action="join" method="post">
<!-- setting up a boundaries to put things on-->
<table border width="400">
<tr>
<td colspan=2 bgcolor="#A3A3A3"><b>Step1 : ID/Password Input</b></td>
</tr>
<tr>
<td>ID: </td>
<td><input type="text" name="id"></td>
</tr>
<tr>
<td>Password: </td>
<td><input type="password" name="pwd"></td>
</tr>
<tr>
<td>Re-type Password: </td>
<td><input type="password" name="pwdCf"></td>
</tr>
<!-- we'll setup servlet to send password and userid to the database so we can compare it to database in server-->
  
<tr><td colspan=2 bgcolor="#A3A3A3"><b>Step2 : Personal information</b></td></tr>
<tr><td>Gender: </td><td><input type="radio" name="gender" value="Male">Male
<input type="radio" name="gender" value="Female">Female</td></tr>
<tr><td>Blood type: </td>
<td><select name="blood" >
  <!-- for selecting multiple options, we should add a line to enable multi-selection, but this is for the blood type. -->
<option value="A형">A형
<option> B형
<option> AB형
<option> O형
  </option>
</select>
</td></tr>
<tr><td>생일:</td> <td><input type="date" name="birth"></td></tr>

<tr><td colspan=2 bgcolor="#A3A3A3"><b>Step3 : 선호도</b></td></tr>
<tr><td>취미:</td><td><input type="checkbox" name="hobby" value="Soccer">Soccer
<input type="checkbox" name="hobby" value="Baseball">Baseball
<input type="checkbox" name="hobby" value="Basketball">Basketball
  </td></tr>
<tr><td>Your favorite color </td><td><input type="color" name="color"></td></tr>

<tr><td colspan=2 bgcolor="#A3A3A3"><b>Step4 : Things you'd like to say</b></td></tr>
<tr><td colspan=2><textarea name = "memo" rows="3" cols="50"></textarea></td></tr>

</table>

<input type="submit" value="submit">
<input type="reset" value="reset"><br>
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

out.print("ID:" + id + "<br>");
out.print("Password: " + pwd + "<br>");
if (!pwd.equals(cf)) out.print("Password does not match. <br>" );
out.print("Gender: " + gender + "<br>");
out.print("blood type: "+blood);
out.print("<br>" + "birthday: " + birth + "<br>");
out.print("Hobby: ");
for (String h:hobby) {
out.print(h + " ");
}
out.print("<br>" +"favorite color: <div style='width:100px;height:100px;background:" + color + "'></div>");
out.print("any last words: ");
out.print(memo);

out.print("</body");
out.print("</html>");

}
