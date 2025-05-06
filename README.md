# GlassHarmonica

```mermaid
---
title: ネイティブアプリ
---
classDiagram
    GameLoop *-- GakufuController
    GameLoop -- Judgement
    Guider -- GakufuController
    GakufuController -- Judgement
    GakufuController -- TouchJudge
    GakufuController "1" o-- "*" Note
    GakufuController -- ChangeController

    class GameLoop {
        <<ゲーム進行全般>>
        + int score
        - int gameState
        - int buttonState
    }
    class GakufuController {
        <<楽譜の進行管理>>
        -List~Note~ notes
        +void StartPlaying()
        +void StopPlaying()
        +void GetTime(int disk)
        -void ReadFromFile(string filename)
    }
    class TouchJudge{
        <<鍵盤の接触判定>>
        - int disk
    }
    class Judgement{
        <<タイミングの評価>>
        +void LetsJudge()
        +void TimeJudge(List~float~ times)
        -void ScoreJudge(float time)
    }
    class ChangeController {
        <<音に関する画面表示>>
        -bool isPlaying[25]
        +void Play(int note)
        +void Stop(int note)
        +void ChangeColor(int note, float duration)
    }
    class Guider {
       <<音符表示>> 
        +void Play(int note)
    }
    class Note {
        <<楽譜上の１音>>
        +float start
        +float duration
        +int note
    }
```mermaid