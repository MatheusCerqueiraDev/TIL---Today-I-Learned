React Router Dom Version 6

Autenticacão

O uso do useNavigate()gancho e do <Navigate>componente para navegar imperativamente após o formulário de login ser enviado
 e declarativamente quando um usuário não autenticado visita uma rota particular.

 O uso de location.statepara preservar o local anterior para que você possa enviar o usuário para lá após a autenticação.

O uso de navigate("...", { replace: true })para substituir a /loginrota na pilha de histórico para que o
 usuário não retorne à página de login ao clicar no botão Voltar após o login.