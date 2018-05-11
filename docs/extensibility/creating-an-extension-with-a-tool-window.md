---
title: ツール ウィンドウで、拡張機能の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f918a5b8b48a7b9553cf3ca2e6c8fe9d38fbc9b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-tool-window"></a>ツール ウィンドウで、拡張機能の作成
この手順では、VSIX プロジェクト テンプレートを使用する方法を説明し、**カスタムのツール ウィンドウ**項目テンプレート、ツール ウィンドウで、拡張機能を作成します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
### <a name="creating-a-tool-window"></a>ツール ウィンドウを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する**最初**です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  プロジェクトを開いたら、という名前のツール ウィンドウの項目テンプレートを追加**MyWindow**です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**カスタムのツール ウィンドウ**します。 **名前**ウィンドウの下部にあるフィールドに、ツール ウィンドウのファイル名に変更**MyWindow.cs**です。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)です。  
  
4.  実験用インスタンスに移動**ビュー/その他のウィンドウ**します。  
  
     メニュー項目を表示する必要があります**MyWindow**です。 クリックします。  
  
     タイトルのツール ウィンドウに表示する必要があります**MyWindow**とボタン言って**Click Me!**