---
layout: LandingPage
title: プロファイルを使用したアプリのパフォーマンスの測定 | Microsoft Docs
description: Visual Studio 2017 を使用して、目的の言語で、アプリケーション、サービス、ツールのパフォーマンスをプロファイリングする方法について説明します。
ms.custom: seodec18
ms.topic: landing-page
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.openlocfilehash: 972e4b8b58229786d403451ddfd7a49a3fe4d6a0
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065546"
---
# <a name="measure-app-performance-in-visual-studio"></a>Visual Studio でアプリのパフォーマンスを測定する

プロファイリングと診断のツールを利用すれば、メモリの利用状況、CPU の利用状況、その他のアプリケーション レベルの問題を診断できます。 これらのツールでは、デバッガーでアプリケーションを実行し、一定期間のデータを集めることができます (変数値、関数呼び出し、イベントなど)。 コードの実行中のさまざまな時点におけるアプリケーションの状態を表示できます。 

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/profiling-feature-tour">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_road-map.svg" alt="Feature Tour of the Profiler">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>プロファイラーの機能ツアー</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/beginners-guide-to-performance-profiling">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_code-performance.svg" alt="Get Started with the Diagnostics Tools (CPU Usage)">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>診断ツールの使用を開始する (CPU 使用率)</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_video.svg" alt="Watch a Video on the Diagnostics Tools">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>診断ツールのビデオを見る</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/memory-usage">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_code-performance.svg" alt="Get Started analyzing Memory Usage">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>メモリ使用量の分析を開始する</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
        <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/application-timeline">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_get-started.svg" alt="Analyze Resource Consumption (XAML)">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>リソース消費量を分析する (XAML)</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/network-usage">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_get-started.svg" alt="Analyze Network Usage (UWP Apps)">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>ネットワーク使用量を分析する (UWP アプリ)</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/visualstudio/debugger/gpu-usage">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_get-started.svg" alt="Analyze GPU Usage (Direct3D)">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>GPU の使用状況を分析する (Direct3D)</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/analyze-energy-use-in-store-apps">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_get-started.svg" alt="Analyze Energy Use (UWP Apps)">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>エネルギー使用を分析する (UWP アプリ)</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/what-s-new-in-profiling-tools">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_whats-new.svg" alt="See What&#39;s New in Profiling Tools">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>「プロファイリング ツールの新機能」を参照してください</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

---
