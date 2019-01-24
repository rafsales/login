<?php

$servidor = '127.0.0.1';
$usuario = 'root';
$senha = '';
$bancoDados = 'curso_php';

$conexao = mysqli_connect ($servidor, $usuario, $senha, $bancoDados) or die(mysqli_error());

mysqli_select_db( $conexao);

if (mysqli_connect_errno ($bancoDados, $conexao)){
    echo "Problemas para conectar no banco. Verifique os dados!";
}else{
    echo "Conexão realizada";
}

$login = $_POST["login"];
$senha = $_POST["senha"];

$selecao = mysqli_query("SELECT * FROM cadastro WHERE login = '$login' AND senha = '$senha' ");

$row = mysqli_fetch_array($selecao);

var_dump($row);

if ($row == "")
{
    echo "<br> logine senha inválidos. </center>";
    echo "<br><br>";
    echo "Volte e tente novamente";
    exit;
} else {
    echo "<br><br>Bem vindo(a) <b>$login</b>";
}

?>
