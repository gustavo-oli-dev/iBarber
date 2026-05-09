# Visão geral
O dono de uma barbearia acessa a plataforma, cria sua conta, personaliza o site com suas cores, logo e informações, e em minutos tem um link exclusivo (ibarber.app.br/sua-barbearia) pronto para receber clientes.

Os clientes acessam o site da barbearia, escolhem o serviço, o barbeiro, o horário e confirmam o agendamento — sem precisar ligar ou mandar mensagem.

# Funcionalidades

## Para o cliente
Agendamento online com seleção de serviço, barbeiro e horário
Login com Google ou e-mail
Cancelamento e reagendamento pelo próprio site
Pagamento via PIX, cartão ou presencialmente
E-mails de confirmação e lembretes automáticos (3 dias, 1 dia, 12h e 1h antes)
Lista de espera para horários lotados

## Para a barbearia
Painel de gestão completo: agenda, clientes, financeiro, relatórios
Personalização total do site: cores, tipografia, logo, fotos, slogan
Gestão de funcionários com horários individuais
Controle de horário de funcionamento por dia da semana
Histórico financeiro com exportação CSV
Notificações de novos agendamentos por e-mail

## Plataforma
Multitenant — cada barbearia completamente isolada
Trial gratuito + planos de assinatura via Mercado Pago
Rate limiting e proteção contra ataques de força bruta
Login social com Google OAuth 2.0

# Tecnologias
Camada	Tecnologia
Backend	Python, Flask, SQLAlchemy
Banco de dados	MySQL (produção), SQLite (desenvolvimento)
Frontend	HTML, CSS, JavaScript puro
Autenticação	Flask Sessions, Google OAuth 2.0
Pagamentos	Mercado Pago Checkout Pro
E-mail	Gmail SMTP
Agendador	APScheduler
Infraestrutura	VPS Linux, Gunicorn, systemd, Cloudflare
Versionamento	Git + GitHub

# Arquitetura
Cliente
└── Cloudflare (DNS + CDN)
└── VPS Linux
├── Gunicorn (WSGI)
│     └── Flask (app principal)
│           ├── Rotas multitenant (por slug)
│           ├── Google OAuth 2.0
│           └── Mercado Pago API
├── MySQL (banco de dados)
└── APScheduler (background)
├── Lembretes de agendamento
├── Verificação de assinaturas
└── Limpeza de contas guest


# Como funciona o multitenant
Cada tenant (barbearia) tem:

Slug único: ibarber.app.br/nome-da-barbearia
Dados completamente isolados no banco
Tema visual independente (cores, fontes, geometria, imagens)
Funcionários, serviços e horários próprios

### Acesse

[ibarber.app.br](https://ibarber.app.br)


