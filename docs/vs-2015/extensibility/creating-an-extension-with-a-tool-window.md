---
title: ツール ウィンドウで拡張機能の作成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afa24a7faceade36cf6b3d19c7e86fb8d6676ba8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534887"
---
# <a name="creating-an-extension-with-a-tool-window"></a>ツール ウィンドウでの拡張機能の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ツール ウィンドウで、拡張機能を作成する](https://docs.microsoft.com/visualstudio/extensibility/creating-an-extension-with-a-tool-window)します。  
  
この手順で、VSIX プロジェクト テンプレートを使用する方法について説明しますと、**カスタム ツール ウィンドウ**ツール ウィンドウで、拡張機能を作成する項目テンプレート。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
### <a name="creating-a-tool-window"></a>ツール ウィンドウの作成  
  
1.  という名前の VSIX プロジェクトを作成する**最初**します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  という名前のツール ウィンドウの項目テンプレートを追加、プロジェクトが開いたら、**最初**します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**カスタム ツール ウィンドウ**します。 **名前**ウィンドウの下部にあるフィールドに、ツール ウィンドウのファイル名を変更して**FirstWindow.cs**します。  
  
3.  プロジェクトをビルドし、デバッグを開始します。  
  
     Visual Studio の実験用インスタンスが表示されます。 実験用インスタンスの詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
4.  実験用のインスタンスに移動**ビュー/その他の Windows**します。  
  
     メニュー項目を表示する必要があります**最初**します。 クリックします。  
  
     タイトルのツール ウィンドウが表示**最初**、ボタン台詞**ここです。**

