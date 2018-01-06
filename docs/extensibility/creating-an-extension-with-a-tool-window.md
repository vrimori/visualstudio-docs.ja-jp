---
title: "ツール ウィンドウで、拡張機能の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4e01959df5da96018aa8f1d06fce1076e732096
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-extension-with-a-tool-window"></a>ツール ウィンドウで、拡張機能の作成
この手順では、VSIX プロジェクト テンプレートを使用する方法を説明し、**カスタムのツール ウィンドウ**項目テンプレート、ツール ウィンドウで、拡張機能を作成します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
### <a name="creating-a-tool-window"></a>ツール ウィンドウを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する**最初**です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  プロジェクトを開いたら、という名前のツール ウィンドウの項目テンプレートを追加**MyWindow**です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**カスタムのツール ウィンドウ**します。 **名前**ウィンドウの下部にあるフィールドに、ツール ウィンドウのファイル名に変更**MyWindow.cs**です。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)です。  
  
4.  実験用インスタンスに移動**ビュー/その他のウィンドウ**します。  
  
     メニュー項目を表示する必要があります**MyWindow**です。 クリックします。  
  
     タイトルのツール ウィンドウに表示する必要があります**MyWindow**とボタン言って**Click Me!**