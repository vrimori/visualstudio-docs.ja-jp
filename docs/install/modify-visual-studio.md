---
title: Visual Studio 2017 の変更 | Microsoft Docs
description: Visual Studio を変更する方法について、ステップ バイ ステップで説明します。
ms.custom: H1Hack27Feb2017
ms.date: 06/12/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: d60603ae9a94e843920f00dc8c8fc2ebb40c8861
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168384"
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>ワークロードやコンポーネントを追加または削除することで Visual Studio 2017 を変更する

実行する作業に合わせて Visual Studio をより簡単にパーソナライズできるようになっただけでなく、Visual Studio をより簡単にカスタマイズできるようにもなりました。 これを行うには、新しい Visual Studio インストーラーを起動して、必要な変更を加えます。

ここではその方法を説明します。

## <a name="modify-workloads"></a>ワークロードの変更

 ワークロードには、使用するプログラミング言語またはプラットフォームに必要な機能が含まれています。 ワークロードを使用することで、必要に応じて、実行する作業に合わせ、Visual Studio を変更できます。

>[!IMPORTANT]
>Visual Studio をインストール、更新、または変更するには、管理アクセス許可を持つアカウントでログオンする必要があります。 詳細については、「[ユーザー アクセス許可と Visual Studio](../ide/user-permissions-and-visual-studio.md)」を参照してください。

1. コンピューター上で Visual Studio インストーラーを見つけます。

     たとえば、Windows 10 を実行しているコンピューター上で、**[スタート]** を選択し、**Visual Studio インストーラー**としてリスト表示される **V** の文字までスクロールします。

     ![Visual Studio インストーラー](media/vs2017-locate-the-visual-studio-installer.PNG "Microsoft Visual Studio インストーラーの検索")

     >[!NOTE]
     >一部のコンピューターでは、Visual Studio インストーラーが **Microsoft Visual Studio インストーラー**として **"M"** の項に表示される場合があります。<br/><br/> Visual Studio インストーラーは `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe` にもあります。

2. インストーラーをクリックまたはタップして起動し、**[変更]** を選択します。

     ![Visual Studio の起動または変更](media/modify-visual-studio.png "Visual Studio 2017 の変更")

     保留中の更新プログラムがある場合、[変更] ボタンは別の場所にあります。 この方法で、更新せずに Visual Studio を変更するならそれができます。 **[詳細]** をクリックして、**[変更]** を選択します。

     ![Visual Studio の更新または変更](media/modify-or-update-visual-studio.png "Visual Studio 2017 の更新または変更")

3. **[ワークロード]** 画面で、インストールまたはアンインストールするワークロードを選択または選択解除します。

    ![Visual Studio 2017 のセットアップ ダイアログ](media/vs2017-modify-workloads.PNG "Visual Studio 2017 でのワークロードの選択")

4. もう一度 **[変更]** を選択します。

5. 新しいワークロードとコンポーネントがインストールされたら、**[起動]** を選択します。

## <a name="modify-individual-components"></a>個々のコンポーネントの変更

便利なワークロード機能を使用せずに Visual Studio のインストールをカスタマイズする場合は、Visual Studio インストーラーで **[個々のコンポーネント]** オプションを選択し、必要なものを選択して、画面の指示に従います。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
