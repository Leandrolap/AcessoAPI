# Sistema de Controle de Acesso com Spring Security e JWT
Este projeto exemplifica a implementação de um sistema de controle de acesso utilizando Spring Security e tokens JWT (JSON Web Token). A aplicação é estruturada para fornecer diferentes níveis de acesso com base nos papéis dos usuários.

# Configuração de Segurança
A classe SecurityConfig configura o Spring Security para a aplicação web:

SecurityFilterChain: Define as regras de segurança HTTP, especificando quais endpoints requerem autenticação e quais são públicos ou acessíveis por diferentes papéis de usuário.

Desativação de CSRF: A proteção CSRF é desabilitada para simplificar a integração com APIs.

UserDetailsService: Implementa três usuários em memória (admin, moderado e comum), utilizando senhas criptografadas com BCrypt.

# Controlador de Autenticação (AuthController)
O AuthController gerencia os endpoints de autenticação:

POST /login: Autentica o usuário com base nas credenciais fornecidas e gera um token JWT por meio do serviço de autenticação (AuthService).

GET /username/{token}: Extrai o nome de usuário do token JWT fornecido, utilizando também o serviço de autenticação.

Endpoints Restritos por Papel:

GET /admin: Acesso permitido apenas para usuários com papel "ADMIN".
GET /moderado: Acesso restrito a usuários com papel "MODERADO".
GET /comum: Acessível a todos os usuários autenticados.
Utilização de JWT (JwtUtil)
A classe JwtUtil contém métodos para gerar e extrair informações de tokens JWT:

Geração de Token: Cria um token JWT com um tempo de expiração configurado para 10 dias.

Extração de Nome de Usuário: Obtém o nome de usuário a partir do token JWT, validando-o com uma chave secreta.

# Serviço de Autenticação (AuthService)
O AuthService fornece métodos para gerar e extrair informações de tokens JWT, encapsulando a lógica relacionada à autenticação e autorização da aplicação.

# Conclusão
Este projeto serve como um exemplo prático de como implementar segurança em uma aplicação web usando Spring Security em conjunto com tokens JWT. Ele demonstra como configurar diferentes níveis de acesso com base em papéis de usuário e como utilizar tokens JWT para autenticar e autorizar usuários de forma eficaz.

Para executar o projeto, é necessário configurar um ambiente de desenvolvimento com as dependências corretas do Spring Security e executar a aplicação em um servidor compatível com Spring Boot.

## Considerações Adicionais
Chave Secreta: A chave secreta utilizada para assinar e verificar tokens JWT deve ser guardada de maneira segura, preferencialmente em variáveis de ambiente ou em um gerenciador de segredos.

Melhorias de Segurança: Em um ambiente de produção real, é recomendável integrar o sistema com um serviço de autenticação centralizado, como OAuth 2.0, e implementar práticas adicionais de segurança, como a utilização de SSL/TLS.

Este projeto é um exemplo educacional que pode ser expandido para atender requisitos específicos de segurança e funcionalidade de aplicações web reais.

# Diagrama de fluxo de Controle de Acesso:
![DIAGRAMA](https://github.com/Leandrolap/ArquiteturadeAplicacoesWeb/assets/12981655/7e97cf1e-1abf-4674-8542-4fb6120b575c)

# Telas de testes:
![Imagem 01](https://github.com/Leandrolap/ArquiteturadeAplicacoesWeb/assets/12981655/6e35a815-4401-41ef-984f-a23c2973c6e8)
![Imagem 02](https://github.com/Leandrolap/ArquiteturadeAplicacoesWeb/assets/12981655/615a7a41-a9b9-4ca1-9fb0-8810a8aa60da)
![Imagem 03](https://github.com/Leandrolap/ArquiteturadeAplicacoesWeb/assets/12981655/6d2fedd5-781b-449c-9c01-3006140521dc)

