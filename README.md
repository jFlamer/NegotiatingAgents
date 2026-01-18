# Multi-Agent Market Simulation using Unity ML-Agents

Projekt realizujący symulację ekonomiczną w środowisku wieloagentowym (MARL - Multi-Agent Reinforcement Learning).

Celem projektu jest zbadanie zachowań emergentnych oraz strategii przetrwania autonomicznych agentów, którzy muszą zarządzać zasobami (Jedzenie, Energia) poprzez handel wymienny, działając pod presją metabolizmu.

---

## Kluczowe Funkcjonalności

* **Autonomiczni Agenci (PPO):** Agenci sterowani siecią neuronową trenowaną algorytmem *Proximal Policy Optimization*. Nauczyli się strategii magazynowania zasobów i handlu hurtowego.
* **Porównanie Strategii:** Implementacja środowiska pozwalającego na bezpośrednie starcie agentów **RL** (sztuczna inteligencja) z agentami **Heurystycznymi** (algorytm "Egoist").
* **Dynamiczna Skalowalność (K-NN):** Zastosowanie algorytmu *K-Nearest Neighbors* pozwala na obsługę zmiennej liczby agentów (testowano dla N=6) przy stałym rozmiarze wejścia sieci neuronowej.
* **Model Fizjologiczny:** System metabolizmu, który wymusza interakcje handlowe.

---

## Wymagania

Aby uruchomić projekt:

1.  **Unity** w wersji **2022.3 LTS** (lub nowszej).
2.  **Python 3.9** lub **3.10** (do obsługi ML-Agents).
3.  Biblioteki Pythona wymienione w `requirements.txt`.

---

## Struktura Projektu

Kluczowe pliki i katalogi w repozytorium:

```text
 NegotiatingAgents
 ┣  requirements.txt           # Lista wymaganych bibliotek Python (do treningu)
 ┣  pliki konfiguracyjne .yaml # Hiperparametry uczenia
 ┣  python_files
 ┃ ┣  DQN_stuff                # pliki treningowe DQN
 ┃ ┗  A2C_stuff                # pliki treningowe A2C
 ┗  Assets
   ┣  Configs                  # Pliki konfiguracyjne YAML dla trenera PPO
   ┃ ┗  JacekConfig.yaml       # Hiperparametry uczenia
   ┣  brains                   # Wytrenowane sieci neuronowe (.onnx)
   ┃ ┗  JacekMaster.onnx       # Finalny model z fazy Self-Play (2.3 mln kroków)
   ┗  Scripts                  # Kod źródłowy C#
     ┣  JacekBrain.cs          # Integracja z ML-Agents (obserwacje, akcje, nagrody)
     ┗  NegotiationAgent.cs    # Główna logika: fizyka, metabolizm, mechanika handlu
```
