---
layout: LandingPage
title: "Visual Studio でのアプリのプロファイル | Microsoft Docs"
description: "Visual Studio 2017 を使用して、目的の言語で、アプリケーション、サービス、ツールのパフォーマンスをプロファイリングする方法について説明します。"
ms.technology: vs-ide-debug
ms.openlocfilehash: fa5b65a11a1275f805644efbc6a210d51c18292d
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="profiling-in-visual-studio"></a>Visual Studio のプロファイル

プロファイリングと診断のツールを利用すれば、メモリの利用状況、CPU の利用状況、その他のアプリケーション レベルの問題を診断できます。 これらのツールでは、デバッガーでアプリケーションを実行し、一定期間のデータを集めることができます (変数値、関数呼び出し、イベントなど)。 コードの実行中のさまざまな時点におけるアプリケーションの状態を表示できます。 

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://docs.microsoft.com/visualstudio/profiling/profiling-feature-tour">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_road-map.svg" alt="">
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
                            <img src="/media/common/i_code-performance.svg" alt="">
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
                            <img src="/media/common/i_video.svg" alt="">
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
                            <img src="/media/common/i_code-performance.svg" alt="">
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
                            <img src="/media/common/i_get-started.svg" alt="">
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
                            <img src="/media/common/i_get-started.svg" alt="">
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
                            <img src="/media/common/i_get-started.svg" alt="">
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
                            <img src="/media/common/i_get-started.svg" alt="">
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
                            <img src="/media/common/i_whats-new.svg" alt="">
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