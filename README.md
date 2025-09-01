# **Calculadora de Manutenção Veicular**

## **📖 Sobre o Projeto**

Esta é uma aplicação web desenvolvida para calcular o custo de manutenção de um veículo com base na quilometragem rodada. O diferencial do cálculo é que o valor final é convertido em litros de combustível, facilitando o pagamento ou reembolso de despesas de forma prática.

O projeto foi construído como uma *Single Page Application* (SPA), onde todos os dados são salvos na nuvem, permitindo que o usuário acesse seu histórico de qualquer dispositivo através de uma autenticação segura com a conta Google.

**🔗 Acesse a aplicação online:** [https://devinfreire.github.io/calculo-manutencao/](https://devinfreire.github.io/calculo-manutencao/)

## **✨ Funcionalidades**

* **🔐 Autenticação com Google:** Login seguro e simplificado para acessar e proteger os dados do usuário.  
* **📝 Adição de Rodagens:** Formulário para adicionar novas viagens, registrando a quilometragem e uma observação opcional.  
* **🕒 Histórico em Tempo Real:** A lista de rodagens é atualizada instantaneamente a cada nova adição, sem a necessidade de recarregar a página.  
* **📊 Totalizador de KM:** Soma automática de toda a quilometragem registrada no histórico.  
* **💰 Cálculo de Custo Final:** Calcula o valor total da manutenção em litros de combustível e seu equivalente em Reais (R$).  
* **☁️ Persistência de Dados na Nuvem:** Todos os dados são salvos no Firebase Firestore, garantindo que não sejam perdidos e possam ser acessados de múltiplos dispositivos.  
* **📱 Design Responsivo:** Interface otimizada para uma experiência de uso agradável tanto em desktops quanto em smartphones.

## **🛠️ Tecnologias Utilizadas**

Este projeto foi construído utilizando tecnologias modernas de desenvolvimento web, com foco em uma arquitetura *serverless* (sem servidor).

* **Frontend:**  
  * **HTML5**  
  * **JavaScript (ES6 Modules)**  
* **Estilização:**  
  * **Tailwind CSS (via CDN):** Para uma estilização rápida, moderna e responsiva.  
* **Backend & Banco de Dados:**  
  * **Google Firebase:** Plataforma utilizada para toda a infraestrutura de backend.  
    * **Firebase Authentication:** Para o sistema de login com provedor Google.  
    * **Firebase Firestore:** Como banco de dados NoSQL para armazenar os dados das rodagens de forma segura e em tempo real.  
* **Hospedagem:**  
  * **GitHub Pages:** Para a publicação e hospedagem gratuita da aplicação.

## **🚀 Como Foi Implementado**

A aplicação é contida em um único arquivo index.html, o que simplifica a hospedagem. A lógica de negócio e a interação com o backend são feitas inteiramente no lado do cliente (client-side) através do JavaScript.

1. **Autenticação:** Ao acessar a página, o usuário é apresentado a uma tela de login. Ao se autenticar com o Google, o Firebase Authentication fornece um ID de usuário (userId) único.  
2. **Estrutura de Dados:** Os dados de cada usuário são armazenados no Firestore em um caminho exclusivo, utilizando o userId para garantir a privacidade e a separação dos dados. A estrutura segue o padrão: /artifacts/{appId}/users/{userId}/trips/{tripId}.  
3. **Segurança:** As **Regras de Segurança (Security Rules)** do Firestore foram configuradas para permitir que um usuário autenticado possa apenas ler e escrever documentos dentro de sua própria pasta de usuário. Qualquer tentativa de acesso a dados de outro usuário é bloqueada diretamente no servidor do Firebase.  
4. **Tempo Real:** A atualização do histórico é feita com o listener onSnapshot do Firestore, que "escuta" por qualquer mudança na coleção de dados do usuário e atualiza a interface automaticamente, proporcionando uma experiência fluida e reativa.