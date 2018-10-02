---
title: フォントと色づけのテキストの色の情報の取得 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d4b5ebbaea2b146f1b853360b88bad2363ce77f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549016"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>フォントと色づけのテキストの色の情報を取得します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を取得するフォントとテキストの色づけのカラー情報](https://docs.microsoft.com/visualstudio/extensibility/getting-font-and-color-information-for-text-colorization)します。  
  
レンダリングまたはユーザー インターフェイス (UI) 要素の色分けされたテキストを表示するプロセスは、プロジェクト、その技術、および開発者の環境設定の種類によって異なります。 **フォントおよび色**プロパティ ページには、設定が格納されます。  
  
 色分けされたテキストを表示するほとんどの実装が必要な`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`表示設定の表示、取得、およびテキストを格納するは、インターフェイスを関連付けられているとします。  
  
> [!NOTE]
>  コア エディターをカスタマイズする際に (サポートする、**テキスト EditorCategory**)、言語サービスでの色分け表示テクノロジを使用することを強くお勧めします。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)します。  
  
## <a name="getting-default-font-and-color-information"></a>既定のフォントおよび色の情報を取得します。  
 すべての**フォントおよび色**でテキストを表示するすべてのウィンドウの設定を指定する必要があります、**表示項目**いずれかの**カテゴリ**します。 詳細については、次を参照してください。[フォントおよび色のオプション ダイアログ ボックス](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)します。  
  
 VSPackage を色分けして表示、現在を取得する必要があります**フォントおよび色**設定します。 VSPackage は、そのニーズに応じて、次の方法でこれを実現できます。  
  
-   フォントおよびカラーの永続化メカニズムを使用して、ストアドまたは現在の状態を取得します。 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)します。  
  
-   使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスのインスタンスを取得するフォントと色のデータを提供するサービスの<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>もフォントおよびカラー プロバイダーが、VSPackage ではないです場合。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> インターフェイスを実装します。  
  
 ポーリングによって得られた結果が最新の状態に日付は、使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスの取得メソッドを呼び出す前に、更新プログラムが必要なかどうかを決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス。  
  
 フォントと色の情報を取得した後、色付けを必要とする要素を識別するために表示されるテキストを解析し、適切なフォントおよび色を使用して、ウィンドウで、テキストを表示します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [フォントとテキストの使用](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [カラーを使用します。](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (グラフィックス デバイス インターフェイス)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

