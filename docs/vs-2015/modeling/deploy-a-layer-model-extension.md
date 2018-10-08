---
title: レイヤー モデル拡張機能の展開 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b5d581ca67a2d3fde5b7acab5937d1aedf88cfa4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535619"
---
# <a name="deploy-a-layer-model-extension"></a>レイヤー モデル拡張機能の配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[レイヤー モデル拡張機能をデプロイ](https://docs.microsoft.com/visualstudio/modeling/deploy-a-layer-model-extension)します。  
  
Visual Studio の他のユーザーは、Visual Studio を使って作成されたレイヤー モデリング拡張機能をインストールできます。  
  
## <a name="installing-your-extension"></a>拡張機能のインストール  
 拡張機能をコンパイルすると VSIX ファイルが作成され、これを他のコンピューターにインストールできます。 また、このファイルを開発用コンピューターにインストールし、Visual Studio のメイン インスタンスで拡張機能を使用できるようにすることもできます。  
  
#### <a name="to-install-the-extension"></a>拡張機能をインストールするには  
  
1.  含むプロジェクトで**source.vsix.manifest**オープン**bin\\ \*** ファイル エクスプ ローラーでします。  
  
2.  コピー、  **\*.vsix**ファイルを拡張機能をインストールするコンピューターにします。  
  
3.  インストール先のコンピューターの Windows エクスプローラーで *.vsix をダブルクリックします。  
  
     VSIX インストーラーが起動します。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新**します。  
  
2.  拡張機能の名前をクリックし、クリックして**アンインストール**します。  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Team Foundation ビルド サーバーへの拡張機能のインストール  
 通常、[!INCLUDE[esprbuild](../includes/esprbuild-md.md)] サーバーには Visual Studio はインストールされていないので、VSIX をダブルクリックしてインストールすることはできません。 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] のインストールには VSIX 拡張機能を実行できるコンポーネントがいくつか含まれますが、拡張機能のインストールは手動で行う必要があります。  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>レイヤー拡張機能を [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] サーバーにインストールするには  
  
1.  コピー、 **.vsix** 、開発用コンピューターからファイルを[!INCLUDE[esprbuild](../includes/esprbuild-md.md)]コンピューター。  
  
     VSIX ファイルを次のいずれかの場所に置きます。  
  
    -   すべてのユーザーおよびサービスを対象にインストールする場合:  
  
         %ProgramFiles%\Microsoft Visual Studio [バージョン]\Common7\IDE\Extensions\Microsoft  
  
    -   [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] を実行するネットワーク サービスだけを対象にインストールする場合:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] が特定のユーザーとして対話モードで実行されるように構成されており、そのユーザーだけを対象にインストールする場合:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[バージョン] \Extensions\Microsoft  
  
        > [!NOTE]
        >  %Localappdata% は通常*DriveName*: ユーザー*UserName*AppDataLocal します。  
  
2.  各 VSIX ファイルを同じ場所のフォルダーに展開します。  
  
    1.  ファイル名拡張子が変更 **.vsix**に **.zip**します。  
  
    2.  .zip ファイルの内容をフォルダーに抽出します。  
  
    3.  .zip ファイルを削除します。  
  
3.  [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] を再起動します。



