<h2 font-size="12px" align="center"> Olá, eu sou Maria 👩‍💻 </h2>
<div> 
  <ul>
    <li> Sou estudante do curso de Análise e Desenvolvimento de Sistemas.</li>
    <li> Iniciei estudando desenvolvimento web com HTML, CSS e JS. Estudei um pouco de desenvolvimento mobile com Kotlin e atualmente estudo desenvolvimento mobile com Swift IOS. </li>
  </ul>
 </div>
 <div align="center"> 
  <img height="150em" src="https://github-readme-stats.vercel.app/api?username=mariafortunato&theme=bear&show_icons=true"/>
  <img height="150em" src = "https://github-readme-stats.vercel.app/api/top-langs/?username=mariafortunato&layout=compact&langs_count=7&theme=bear"/>
</div>

## <div>
   <a href="https://www.linkedin.com/in/marialicefortunato/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"/>
   </a> 
   <a href="mailto:malice.rfort@gmail.com" target="_blank">
     <img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"/>
   </a>   
   <a href="https://t.me/mariafortunato"> 
     <img src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" target="_blank"/>
   </a>
   
</div>
<!DOCTYPE html>
<html>
<head>
	<meta charset=utf-8 />
	<title>Contador de Visitas</title>

</head>
<body>

<?php

	function get_num_visitas(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}
		
		mysql_select_db("contador");
		$query = "SELECT total " .
				 "FROM `visitas` " .
				 "ORDER BY total ASC LIMIT 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		if (mysql_num_rows($result) == 0) {
			echo "No rows found, nothing to print so am exiting";
			exit;
		}
		$row = mysql_fetch_array($result);
		mysql_close($link);
		return $row["total"];
		//fazer consulta
		//retornar total
	}

	function imprime_visitas($contador){
		return "<h1>" . $contador . "</h1>";
	}
	
	function contar_visita(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}
		
		mysql_select_db("contador");
		$query = "UPDATE `visitas` " .
				 "SET total = total + 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		mysql_close($link);
	}

	contar_visita();
	$contador = get_num_visitas();
	echo imprime_visitas($contador);

?>

 
</body>
</html>
