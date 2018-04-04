---
title: Visual Studio 2017 の変更 | Microsoft Docs
description: Visual Studio を変更する方法について、ステップ バイ ステップで説明します。
ms.custom: H1Hack27Feb2017
ms.date: 11/08/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 597da9be2ce4c6d22beaa6fc5fc419ef785ece94
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>ワークロードやコンポーネントを追加または削除することで Visual Studio 2017 を変更する
実行する作業に合わせて Visual Studio をより簡単にカスタマイズできるようになっただけでなく、Visual Studio をより簡単にカスタマイズできるようにもなりました。 これまでのようにコントロール パネルに移動する必要はありません。代わりに新しい Visual Studio インストーラーを起動して、必要な変更を加えます。

ここではその方法を説明します。  

## <a name="modify-workloads"></a>ワークロードの変更  
 ワークロードには、使用するプログラミング言語またはプラットフォームに必要な機能が含まれています。 ワークロードを使用することで、必要に応じて、実行する作業に合わせ、Visual Studio を変更できます。  

>[!IMPORTANT]
>Visual Studio をインストール、更新、または変更するには、管理アクセス許可を持つアカウントでログオンする必要があります。 詳細については、「[ユーザー アクセス許可と Visual Studio](../ide/user-permissions-and-visual-studio.md)」を参照してください。

1.  コンピューター上で Visual Studio インストーラーを見つけます。  

     たとえば、Windows 10 Anniversary Update を実行しているコンピューター上では、**[スタート]** を選択し、**Visual Studio インストーラー**としてリスト表示される **V** の文字までスクロールします。  

     ![Visual Studio インストーラー](media/vs2017-locate-the-visual-studio-installer.PNG "Microsoft Visual Studio インストーラーの検索")

     >[!NOTE]
     一部のコンピューターでは、Visual Studio インストーラーが **Microsoft Visual Studio インストーラー**として **"M"** の項に表示される場合があります。<br/><br/> Visual Studio インストーラーは `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe` にもあります。

2.  インストーラーをクリックまたはタップして起動し、**[変更]** を選択します。  

     ![Visual Studio の起動または変更](media/vs2017-modify.PNG "Visual Studio 2017 の変更")  

3.  **[ワークロード]** 画面で、インストールまたはアンインストールするワークロードを選択または選択解除します。  

    ![Visual Studio 2017 のセットアップ ダイアログ](media/vs2017-modify-workloads.PNG "Visual Studio 2017 でのワークロードの選択")

4. もう一度 **[変更]** をクリックまたはタップします。  

5. 新しいワークロードとコンポーネントがインストールされたら、**[起動]** をクリックします。

## <a name="modify-individual-components"></a>個々のコンポーネントの変更

便利なワークロード機能を使用せずに Visual Studio のインストールをカスタマイズする場合は、Visual Studio インストーラーで **[個々のコンポーネント]** オプションを選択し、必要なものを選択して、画面の指示に従います。  

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
