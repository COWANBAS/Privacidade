# LOCALIZAÇÃO

Bloqueio de localização oferece uma vantagem significativa em termos de privacidade e segurança do usuário na internet. Ao sobrescrever as funções getCurrentPosition e watchPosition do objeto navigator.geolocation, ele impede que sites acessem a localização geográfica do usuário sem sua permissão explícita. Isso significa que suas informações de localização não serão compartilhadas inadvertidamente com sites que podem usá-las para rastreamento, publicidade direcionada ou outros fins potencialmente invasivos. Com esse script ativado, você tem maior controle sobre sua privacidade online, garantindo que sua localização permaneça protegida e fora do alcance de terceiros não autorizados.

*Sobrescrevendo GetCurrentPosition*

Sobrescreve a função navigator.geolocation.getCurrentPosition. Normalmente, essa função é usada para obter a localização atual do usuário. No entanto, aqui estamos modificando seu comportamento para que ela sempre retorne um erro, impedindo o acesso à localização.

![image](https://github.com/user-attachments/assets/f06251db-585b-46f7-9469-094e64bade12)

*Sobrescrevendo WatchPosition e Fechando a Função Autoexecutável*

Sobrescreve a função navigator.geolocation.watchPosition. Esta função é usada para receber atualizações periódicas da localização do usuário. Mais uma vez, estamos modificando seu comportamento para que ela sempre retorne um erro.

![image](https://github.com/user-attachments/assets/91b9998e-8536-4739-aa43-064141d4ffdb)

# BLOQUEAR MICROFONE

É útil para usuários preocupados com a privacidade e segurança de seus dispositivos, garantindo que apenas sites confiáveis possam acessar o microfone.

"Sobrescrita Função getUserMedia"

O script sobrescreve a função "getUserMedia" do objeto "navigator.mediaDevices", função "getUserMedia" é usada pelos sites para solicitar acesso a dispositivos de mídia, como o microfone e a câmera.

![image](https://github.com/user-attachments/assets/8c65e2c2-9f31-4432-80a8-07fc2b2ecd6a)

"Verificar a Restrições de Áudio"

O script verifica se as restrições "constraints" incluem audio, Se o audio estiver presente, a promessa é rejeitada com o erro "Acesso negado", se audio não estiver presente, o script permite o acesso à mídia solicitada, chamando a função original "getUserMedia"

![image](https://github.com/user-attachments/assets/2b45b016-8e08-44c7-8240-0baec43f4bf8)

"Salvando a Função Original"

A função original "getUserMedia" é salva em "navigator.mediaDevices.originalGetUserMedia" para que possa ser usada para outras mídias, como vídeo.

![image](https://github.com/user-attachments/assets/50d5cb30-04b6-4dfa-b09d-f3bd3f0dc834)

"BENEFICIOS"

* Privacidade: Impede que sites acessem o microfone do usuário sem permissão explícita, aumentando a privacidade.

* Segurança: Reduz o risco de espionagem ou gravação não autorizada através do microfone.

* Controle: Dá ao usuário mais controle sobre quais sites podem acessar seu microfone.

* Flexibilidade: Permite exceções, como no caso de discord.com, onde o acesso ao microfone ainda é permitido.

# CAMERA 

"Sobrescrevendo navigator.mediaDevices.getUserMedia"

![image](https://github.com/user-attachments/assets/8fa3691d-b2cd-4776-8895-5ebb35f6b856)

(navigator.mediaDevices && navigator.mediaDevices.getUserMedia): Verifica se o objeto navigator.mediaDevices e a função getUserMedia existem. Isso é importante para garantir que o código só tente sobrescrever a função se ela realmente existir.
Armazenar a Função Original:

"const originalGetUserMedia = navigator.mediaDevices.getUserMedia.bind(navigator.mediaDevices)"

Armazena a função original getUserMedia para que ainda possamos chamar a funcionalidade original se necessário.
Sobrescrever a Função:

navigator.mediaDevices.getUserMedia = function (constraints) {...}: Sobrescreve a função getUserMedia com uma nova função que verifica os constraints (restrições) passados para a função.

"Bloquear Acesso à Câmera"

"(constraints && constraints.video) { return Promise.reject(new Error('Acesso à câmera bloqueado.'))"

Se as restrições incluem video, a função retorna uma Promise rejeitada com a mensagem "Acesso à câmera bloqueado.

"Return originalGetUserMedia(constraints)"

Se as restrições não incluem video, a função original getUserMedia é chamada com as mesmas restrições.
Esse userscript bloqueia qualquer tentativa de acessar a câmera do computador sobrescrevendo a função navigator.mediaDevices.getUserMedia. Se um site tentar acessar a câmera, a função modificada rejeitará a tentativa e retornará um erro.
O script oferece vantagens significativas para usuários preocupados com a privacidade e a segurança de suas câmeras nos computadores.
