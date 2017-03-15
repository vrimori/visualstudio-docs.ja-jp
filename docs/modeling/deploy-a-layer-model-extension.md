---
title: "レイヤー モデル拡張機能の展開 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 27
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 03164fe80a0b8f4dbc321a7e57b7db9e38e405d5
ms.lasthandoff: 02/22/2017

---
# <a name="deploy-a-layer-model-extension"></a>レイヤー モデル拡張機能の配置
Visual Studio の他のユーザーは、Visual Studio を使って作成されたレイヤー モデリング拡張機能をインストールできます。  
  
## <a name="installing-your-extension"></a>拡張機能のインストール  
 拡張機能をコンパイルすると VSIX ファイルが作成され、これを他のコンピューターにインストールできます。 また、このファイルを開発用コンピューターにインストールし、Visual Studio のメイン インスタンスで拡張機能を使用できるようにすることもできます。  
  
#### <a name="to-install-the-extension"></a>拡張機能をインストールするには  
  
1.  含むプロジェクトで**source.vsix.manifest**、開かれている**bin\\ \* **エクスプ ローラーでします。  
  
2.  コピー、 ** \*.vsix**拡張機能をインストールするコンピューターへのファイルです。  
  
3.  インストール先のコンピューターの Windows エクスプローラーで *.vsix をダブルクリックします。  
  
     VSIX インストーラーが起動します。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新プログラム**します。  
  
2.  拡張機能の名前をクリックし、クリックして**アンインストール**します。  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Team Foundation ビルド サーバーへの拡張機能のインストール  
 通常、[!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] サーバーには Visual Studio はインストールされていないので、VSIX をダブルクリックしてインストールすることはできません。 
          [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] のインストールには VSIX 拡張機能を実行できるコンポーネントがいくつか含まれますが、拡張機能のインストールは手動で行う必要があります。  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>レイヤー拡張機能を [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] サーバーにインストールするには  
  
1.  コピー、 **.vsix** 、開発用コンピューターからのファイル、[!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]コンピューター。  
  
     VSIX ファイルを次のいずれかの場所に置きます。  
  
    -   すべてのユーザーおよびサービスを対象にインストールする場合:  
  
         %ProgramFiles%\Microsoft Visual Studio [バージョン]\Common7\IDE\Extensions\Microsoft  
  
    -   
          [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] を実行するネットワーク サービスだけを対象にインストールする場合:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[バージョン] \Extensions\Microsoft  
  
    -   
          [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] が特定のユーザーとして対話モードで実行されるように構成されており、そのユーザーだけを対象にインストールする場合:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[バージョン] \Extensions\Microsoft  
  
        > [!NOTE]
        >  %Localappdata% は通常、 *DriveName*: ユーザー*UserName*AppDataLocal します。  
  
2.  各 VSIX ファイルを同じ場所のフォルダーに展開します。  
  
    1.  ファイル名拡張子を変更する**.vsix**に**.zip**します。  
  
    2.  .zip ファイルの内容をフォルダーに抽出します。  
  
    3.  .zip ファイルを削除します。  
  
3.  
          [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] を再起動します。

