---
title: "Visual Studio 管理者ガイド | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 69ac1327fa9233bf0ecc18be5e7d2f2a4f82b3b0
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Visual Studio 2017 の管理者ガイド

Visual Studio をネットワークに配置するには、インストール対象となる各コンピューターが[最小インストール要件](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)を満たしている必要があります。 --layout スイッチを指定してセットアップ ファイルを実行し (「[Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)」ページの説明を参照)、そのファイルをローカル コンピューターからネットワーク共有にコピーすることで、ネットワーク共有を作成できます。   

 ネットワーク共有からのインストールは、出所のソースの場所を記憶します。 これは、クライアント マシンの修復に、クライアントのインストール元のネットワーク共有に戻る必要があることを意味します。 ネットワークの場所は、Visual Studio 2017 クライアントが組織で実行されると予想される有効期間に合わせて配置されるよう慎重に選択してください。

## <a name="tools"></a>ツール

 Visual Studio のインストールの管理をサポートする次のようなツールを用意しています。

* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): ユーザーが使用しているマシンで VS インスタンスを問い合わせるのに役立つ C# および C++ のサンプル。
* [VSWhere](https://github.com/microsoft/vswhere): Visual Studio のコア ツールを探すのに役立つ C++ の .exe。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): セットアップに関連する一般的な管理タスク用の強力な PowerShell スクリプト。


## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio のワークロード ID とコンポーネント ID を使用してオフライン インストールをカスタマイズする](workload-and-component-ids.md)
* [Visual Studio 2017 で問題を報告する](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

