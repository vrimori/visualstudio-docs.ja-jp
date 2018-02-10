---
title: "レイヤー モデル拡張機能の配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 311add860016c914aab232ffad6e3a4efadb15c9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="deploy-a-layer-model-extension"></a>レイヤー モデル拡張機能の配置
Visual Studio の他のユーザーは、Visual Studio を使って作成されたレイヤー モデリング拡張機能をインストールできます。  
  
## <a name="installing-your-extension"></a>拡張機能のインストール  
 拡張機能をコンパイルすると VSIX ファイルが作成され、これを他のコンピューターにインストールできます。 また、このファイルを開発用コンピューターにインストールし、Visual Studio のメイン インスタンスで拡張機能を使用できるようにすることもできます。  
  
#### <a name="to-install-the-extension"></a>拡張機能をインストールするには  
  
1.  含むプロジェクトで**source.vsix.manifest**、開かれている**bin\\ \*** ファイル エクスプ ローラーでします。  
  
2.  コピー、  **\*.vsix**ファイルを拡張機能をインストールするコンピューターにします。  
  
3.  インストール先のコンピューターの Windows エクスプローラーで *.vsix をダブルクリックします。  
  
     VSIX インストーラーが起動します。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新プログラム**です。  
  
2.  拡張機能の名前をクリックし、クリックして**アンインストール**です。  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Team Foundation ビルド サーバーへの拡張機能のインストール  
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] サーバーは通常どおり Visual Studio がインストールされておらずためをダブルクリックして、VSIX をインストールすることはできません。 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] のインストールには VSIX 拡張機能を実行できるコンポーネントがいくつか含まれますが、拡張機能のインストールは手動で行う必要があります。  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>レイヤー拡張機能を [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] サーバーにインストールするには  
  
1.  コピー、 **.vsix** 、開発用コンピューターからのファイル、[!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]コンピューター。  
  
     VSIX ファイルを次のいずれかの場所に置きます。  
  
    -   すべてのユーザーおよびサービスを対象にインストールする場合:  
  
         %ProgramFiles%\Microsoft Visual Studio [バージョン]\Common7\IDE\Extensions\Microsoft  
  
    -   [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] を実行するネットワーク サービスだけを対象にインストールする場合:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] が特定のユーザーとして対話モードで実行されるように構成されており、そのユーザーだけを対象にインストールする場合:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
        > [!NOTE]
        >  通常 %localappdata% *DriveName*: ユーザー*UserName*AppDataLocal です。  
  
2.  各 VSIX ファイルを同じ場所のフォルダーに展開します。  
  
    1.  ファイル名拡張子が変更**.vsix**に**.zip**です。  
  
    2.  .zip ファイルの内容をフォルダーに抽出します。  
  
    3.  .zip ファイルを削除します。  
  
3.  [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] を再起動します。
