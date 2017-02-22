---
title: "ツール ウィンドウで、拡張機能を作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# ツール ウィンドウで、拡張機能を作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この手順では、VSIX プロジェクト テンプレートを使用する方法を説明し、 **カスタム ツール ウィンドウ** ツール ウィンドウで、拡張機能を作成する項目テンプレートです。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
### ツール ウィンドウを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する **最初**します。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#\/機能拡張**します。  
  
2.  プロジェクトを開いたら、という名前のツール ウィンドウの項目テンプレートを追加 **最初**します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **カスタム ツール ウィンドウ**します。**名** ウィンドウの下部にあるフィールドに、ツール ウィンドウ ファイル名を変更 **FirstWindow.cs**します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用インスタンスでに移動 **ビュー\/その他のウィンドウ**します。  
  
     メニュー項目が表示 **最初**します。 クリックします。  
  
     タイトルのツール ウィンドウが表示されます **最初** とボタン言って **Click Me\!.**