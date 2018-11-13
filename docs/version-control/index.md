---
layout: LandingPage
title: バージョン管理
description: Visual Studio でバージョン コントロールを始めるためのガイド
keywords: VSTS, TFS, バージョン コントロール
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 3640fba7d1ca3993841adb94dfdd08bc7d405e9b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348163"
---
# <a name="version-control-in-visual-studio"></a>Visual Studio でのバージョン コントロール

バージョン コントロール システムは、コードに徐々に加えた変更を追跡するのに役立ちます。 ユーザーが変更を行うと、バージョン コントロール システムによってファイルのスナップショットが取得されます。 バージョン コントロール システムはスナップショットを永続的に保存するので、後で必要なときに呼び戻すことができます。 Visual Studio では、[Git](/azure/devops/repos/git/index?view=vsts) と [Team Foundation バージョン管理 (TFVC)](/azure/devops/repos/tfvc/index?view=vsts) を利用できます。 この 2 つのシステムのどちらかに決めるには、「[Choosing the right version control for your project (プロジェクトに適切なバージョン コントロールの選択)](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json)」をご覧ください。

## <a name="git"></a>Git

Git は現在、最も使用されているバージョン コントロール システムであり、バージョン コントロールの標準になりました。 Git は分散型バージョン コントロール システムであり、コードのローカル コピーが完全なバージョン コントロール リポジトリになります。 このように完全な機能を備えたローカル リポジトリによって、オフラインまたはリモートでの作業が容易になりました。 作業をローカルでコミットし、次にリポジトリのコピーをサーバー上のコピーに同期させます。 このパラダイムは、コードの新しいバージョンを作成する前にクライアントがコードをサーバーと同期する必要のある集中型バージョン コントロールとは異なります。

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Git についての情報</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Visual Studio での Git の概要</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>既存の Git リポジトリを複製する</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Team Foundation バージョン管理 (TFVC) は、一元化されたバージョン管理システムです。 通常、チーム メンバーの開発用コンピューターには、各ファイルの 1 つのバージョンだけが存在します。 履歴データはサーバーにのみ保持されます。 分岐はパスに基づき、サーバー上で作成されます。

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>TFVC についての情報</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Visual Studio で TFVC の使用を開始する</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>コードの確認</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="resources"></a>リソース

- [Pro Git ブック](https://git-scm.com/book/en/v2)
- [Git への移行を計画する](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [TFVC から Git への移行](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)
- [バージョン コントロール (Visual Studio for Mac)](/visualstudio/mac/version-control)