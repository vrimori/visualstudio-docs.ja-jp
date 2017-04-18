---
title: "フォントとテキスト彩色の色の情報を取得する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 57b3d53f86d132779fb00608886fa7c479b71551
ms.lasthandoff: 04/05/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>フォントとテキスト彩色の色の情報を取得します。
レンダリングまたはユーザー インターフェイス (UI) 要素の色分けされたテキストを表示するプロセスは、プロジェクト、テクノロジ、および developer の基本設定の種類によって異なります。 **フォントおよび色**プロパティ ページの設定を保存します。  
  
 色分けされたテキストを表示するほとんどの実装が必要な`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`表示設定の表示、取得、およびテキストを格納するためのインターフェイスを関連付けられているとします。  
  
> [!NOTE]
>  コア エディターをカスタマイズするとき (がサポートする、**テキスト EditorCategory**)、言語サービスでは、色分けテクノロジを使用することを強くお勧めします。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)です。  
  
## <a name="getting-default-font-and-color-information"></a>既定のフォントと色の情報を取得します。  
 すべての**フォントおよび色**でテキストを表示するすべてのウィンドウの設定を指定する必要があります、**表示項目**いずれかの**カテゴリ**です。 詳細については、次を参照してください。[フォントおよび色のオプション ダイアログ ボックス](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)です。  
  
 VSPackage、色分けして表示する現在を取得する必要があります**フォントおよび色**設定します。 VSPackage は、そのニーズに応じて、次の方法でこれを達成できます。  
  
-   フォントおよびカラーの永続化メカニズムを使用して、ストアドまたは現在の状態を取得します。 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)です。  
  
-   使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>のインスタンスを取得するフォントと色のデータを提供するサービスのインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>もフォントおよびカラー プロバイダーが、VSPackage ではない場合は、</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 。  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>。  
  
 確実にポーリングによって取得される結果は最新の状態に日付を使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスの取得方法を呼び出す前に、更新が必要なかどうかを決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>。  
  
 フォントと色の情報を取得した後、色付けを必要とする要素を識別する表示されるテキストを解析し、適切なフォントと色を使用して、ウィンドウでテキストを表示します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [フォントとテキストを使用します。](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [カラーを使用します。](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (グラフィックス デバイス インターフェイス)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
