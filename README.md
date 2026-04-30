# Desafio-FTP-Web-SMB-
Wordlists Utilizadas:

Arquivo               Conteúdo (Exemplos)	                                        Finalidade

users.txt	      admin, root, user, msfadmin	                      Identificação de contas de sistema e serviço.
pass.txt	      123456, password, msfadmin, admin	                  Teste de senhas fracas e padrões de fábrica.





medusa -h 192.168.56.101 -u admin -P pass.txt -M http -m DIR:/dvwa/vulnerabilities/brute/
Validação de Acesso: O acesso é validado quando o Medusa retorna a mensagem SUCCESS . Para confirmar, realizei um acesso manual via terminal: ftp 192.168.56.101.    


**tive um problema que o medusa teve um erro de modulo, então migrei pra hydra**
Serviço: SMB (Porta 445)
Enumeração prévia: nmap -p 445 --script smb-enum-users 192.168.56.101`
Comando (Password Spraying):
bash medusa -h 192.168.56.101 -U users.txt -p msfadmin -M smbnt
Validação de Acesso: O Medusa confirmou a validade da senha em múltiplas contas enumeradas.

    

Recomendações de Mitigação (Prevenção)

Para proteger o ambiente contra os ataques simulados acima, as seguintes medidas são recomendadas:

Políticas de Bloqueio: Configurar o sistema para bloquear temporariamente contas ou endereços IP após X tentativas falhas 
Complexidade de Senhas: Implementar requisitos mínimos (mínimo 12 caracteres, uso de símbolos e números) para inviabilizar o uso de wordlists simples.
Desabilitar Enumeração de Usuários: Configurar o serviço SMB para não responder a requisições de listagem de usuários anônimos 





