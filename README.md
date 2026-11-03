[README.md](https://github.com/user-attachments/files/34338027/README.md)
<div align="center">

# 🎀👑 Quiz da Patixa Teló 👑🎀

### *Será que você é fã de verdade?* ✨

Um jogo de perguntas e respostas **kawaii** feito em **Kotlin + Jetpack Compose**,
com pontuação, cronômetro, categorias e ranking local. 💖

![Kotlin](https://img.shields.io/badge/Kotlin-2.0.21-FF6FA5?style=for-the-badge&logo=kotlin&logoColor=white)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-Material%203-E0457F?style=for-the-badge&logo=jetpackcompose&logoColor=white)
![Android](https://img.shields.io/badge/Android-8.0%2B-FFB3D1?style=for-the-badge&logo=android&logoColor=white)
![Status](https://img.shields.io/badge/status-pronto%20pra%20jogar-C9B6FF?style=for-the-badge)

</div>

---

## 🌸 Sobre o projeto

Projeto educacional que pratica os fundamentos de **Compose** e de **gerenciamento de estado** em um quiz completo.
O tema do jogo é a influenciadora **Patixa Teló**, a "Rainha do Amazonas", com perguntas sobre sua trajetória, seus memes e suas aparições na TV.

> 💬 Projeto de fã, sem fins lucrativos e **não oficial**. Não tem ligação com a Patixa Teló, com sua equipe ou com qualquer emissora. As perguntas foram montadas a partir de reportagens públicas.

---

## ✨ Funcionalidades

| | Recurso | Detalhes |
|---|---|---|
| 🎯 | **Modos de jogo** | Partidas de **10, 15 ou 20** perguntas |
| 📝 | **5 alternativas** | Seleção única com `RadioButton` |
| 🔒 | **Resposta única** | Depois de confirmar, a questão trava e não aceita outra resposta |
| 📊 | **Progresso** | Barra de progresso e contador "Pergunta X de Y" |
| ⏰ | **Tempo limite** | 20 segundos por pergunta; acertar rápido rende mais pontos |
| ⭐ | **Pontuação** | 10 pontos por acerto + bônus de velocidade |
| ✅❌ | **Resultado** | Acertos, erros, aproveitamento e pontuação final |
| 🏆 | **Ranking local** | Top 10 salvo no aparelho com `SharedPreferences` |
| 🔁 | **Reiniciar** | Jogue de novo com perguntas sorteadas e embaralhadas |
| 🎀 | **Tema kawaii** | Visual rosinha, cantos arredondados, emojis e degradê |

### 🗂️ Categorias

- 👑 Quem é ela
- 📺 TV e Reality
- 💬 Memes e Frases
- 🗺️ Lugares e Festas
- ✨ Curiosidades

O banco tem **25 perguntas**, sorteadas e embaralhadas a cada partida.

---

## 🧠 Conceitos trabalhados

`RadioButton` • `Column` • `Button` • `data class` • `List` • `rememberSaveable`

Além deles, o projeto usa:

- `LaunchedEffect` para o cronômetro por pergunta
- `SharedPreferences` para o ranking local
- `Modifier.selectable` com `Role.RadioButton` para boa acessibilidade
- Estado que sobrevive à rotação de tela, usando `rememberSaveable` e uma *seed* para regerar o mesmo quiz

---

## 🚀 Como rodar

### Pré-requisitos

- [Android Studio](https://developer.android.com/studio) (Panda ou mais recente)
- JDK 11+ (já vem com o Android Studio)
- Celular ou emulador com **Android 8.0 (API 26)** ou superior

### Passo a passo

```bash
# 1. Clone o repositório
git clone https://github.com/SEU-USUARIO/QuizPatixa.git

# 2. Abra a pasta no Android Studio
#    File → Open → QuizPatixa
```

3. Espere o **Gradle sincronizar** (a primeira vez precisa de internet).
4. Aperte **Run ▶** no emulador ou no celular.

> 💡 Se o Android Studio sugerir atualizar o plugin do Android (AGP), pode aceitar.

---

## 🧩 Estrutura do projeto

```
QuizPatixa/
├── app/
│   ├── build.gradle.kts
│   └── src/main/
│       ├── AndroidManifest.xml
│       ├── java/com/example/quizpatixa/
│       │   └── MainActivity.kt      # app inteiro: dados, telas e lógica
│       └── res/                     # ícone, cores, strings e tema
├── build.gradle.kts
├── settings.gradle.kts
└── gradle.properties
```

### Organização do `MainActivity.kt`

| Seção | O que faz |
|---|---|
| `data class Question` / `RankEntry` | Modelos de dados |
| `questionBank` | Banco com as 25 perguntas |
| `RankingStore` | Salva e carrega o top 10 |
| `PatixaQuizApp` | Estado e navegação entre as telas |
| `MenuScreen` | Apelido, escolha de 10/15/20 perguntas e início |
| `QuizScreen` | Pergunta, alternativas, tempo e progresso |
| `ResultScreen` | Placar final |
| `RankingScreen` | Lista dos melhores jogadores |

---

## ➕ Como adicionar perguntas

Abra o `MainActivity.kt` e adicione uma linha na lista `questionBank`.
**A primeira alternativa é sempre a correta**; o app embaralha sozinho.

```kotlin
q("Curiosidades ✨",
  "Sua pergunta aqui?",
  "Resposta certa",          // ✅ sempre a primeira
  "Errada 1", "Errada 2", "Errada 3", "Errada 4")
```

Cada pergunta precisa ter **exatamente 5 alternativas**, todas diferentes entre si.

Para mudar o tempo por pergunta, altere a constante:

```kotlin
private const val TIME_PER_QUESTION = 20 // segundos
```

---

## 🎨 Paleta de cores

| Cor | Hex | Uso |
|---|---|---|
| 🌸 Pink | `#FF6FA5` | Botões e destaques |
| 💗 Pink Dark | `#E0457F` | Títulos e textos de destaque |
| 🍬 Pink Light | `#FFD6E7` | Bordas e fundos suaves |
| 💜 Lavender | `#E9D8FF` | Etiquetas e degradê |
| 🍃 Mint | `#CFF5E3` | Resposta certa |
| 🍒 Rose | `#FFCDD2` | Resposta errada |

---

## 🛠️ Tecnologias

- **Kotlin** 2.0.21
- **Jetpack Compose** com **Material 3** (Compose BOM 2024.09.00)
- **Android Gradle Plugin** 8.13
- `minSdk 26` • `targetSdk 36`

---

## 🗺️ Ideias para o futuro

- [ ] Mais perguntas e novas categorias
- [ ] Efeitos sonoros e animações de acerto e erro
- [ ] Modo escuro kawaii 🌙
- [ ] Compartilhar o resultado nas redes
- [ ] Salvar o ranking na nuvem
- [ ] Níveis de dificuldade

---

## 🤝 Contribuindo

Contribuições são muito bem-vindas! 💕

1. Faça um **fork** do projeto
2. Crie uma branch: `git checkout -b minha-feature`
3. Faça o commit: `git commit -m "feat: minha feature"`
4. Envie: `git push origin minha-feature`
5. Abra um **Pull Request**

---

## 📄 Licença

Distribuído sob a licença **MIT**. Veja o arquivo `LICENSE` para mais informações.

---

<div align="center">

Feito com 💖 e muito rosa
**Quiz da Patixa Teló** • Projeto de fã, não oficial

🎀 ⭐ Se você gostou, deixe uma estrela no repositório! ⭐ 🎀

</div>
