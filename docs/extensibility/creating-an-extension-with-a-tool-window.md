---
title: ツール ウィンドウで拡張機能の作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e21c49971660f32abef3a47e436d01e5af05543
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838993"
---
# <a name="create-an-extension-with-a-tool-window"></a>ツール ウィンドウでの拡張機能を作成します。
この手順で、VSIX プロジェクト テンプレートを使用する方法について説明しますと、**カスタム ツール ウィンドウ**ツール ウィンドウで、拡張機能を作成する項目テンプレート。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
### <a name="create-a-tool-window"></a>ツール ウィンドウを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する**最初**します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** > **Extensibility**します。  
  
2.  という名前のツール ウィンドウの項目テンプレートを追加、プロジェクトが開いたら、 **MyWindow**します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#** > **拡張**選択と**カスタム ツール ウィンドウ**。 **名前**ウィンドウの下部にあるフィールドに、ツール ウィンドウのファイル名を変更して*MyWindow.cs*します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。[実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用のインスタンスに移動**ビュー** > **その他の Windows**します。  
  
     メニュー項目を表示する必要があります**MyWindow**します。 クリックします。  
  
     タイトルのツール ウィンドウが表示**MyWindow** 、ボタン台詞**ここです。**