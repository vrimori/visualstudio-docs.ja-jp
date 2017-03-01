---
title: "フォントとテキストの色づけの色情報の取得 |Microsoft ドキュメント"
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: d0b3d50ab2a78bf806be8c7339bb260746e1c457
ms.lasthandoff: 02/22/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>フォントとテキストの色づけの色の情報を取得します。
レンダリングまたはユーザー インターフェイス (UI) 要素に色を指定したテキストを表示するプロセスは、プロジェクト、テクノロジ、および開発者の環境設定の種類によって異なります。 **フォントおよび色**プロパティ ページの設定を保存します。  
  
 色分けされたテキストが表示されるほとんどの実装が必要な`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`表示設定の表示、取得、およびテキストを格納するためのインターフェイスを関連付けられているとします。  
  
> [!NOTE]
>  コア エディターをカスタマイズするときに (がサポートする、**テキスト EditorCategory**)、言語サービスでの色分け表示テクノロジを使用することを強くお勧めします。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)します。  
  
## <a name="getting-default-font-and-color-information"></a>既定のフォントと色の情報を取得します。  
 すべての**フォントおよび色**でテキストを表示するすべての期間の設定を指定してください、**表示項目**いずれかの**カテゴリ**します。 詳細については、次を参照してください。[フォントや色のオプション ダイアログ ボックス](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)します。  
  
 VSPackage での色分けに現在を取得する必要があります**フォントおよび色**設定します。 VSPackage は、そのニーズに応じて、次の方法でこれを実現できます。  
  
-   フォントと色の永続化メカニズムを使用すると、蓄積または現在の状態を取得できます。 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)します。  
  
-   使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>のインスタンスを取得するフォントおよび色のデータを提供するサービスのインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>VSPackage とは異なるフォントおよびカラー プロバイダーの場合は、</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 。  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>。  
  
 ポーリングによって得られた結果が最新であるを使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>の取得方法を呼び出す前に、更新プログラムが必要なかどうかを判断するインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>。  
  
 フォントと色の情報を取得した後、色付けを必要とする要素を識別するために表示されるテキストを解析し、適切なフォントおよび色を使用してウィンドウのテキストが表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [フォントとテキストの使用](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [色の調整](/visual-cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (グラフィックス デバイス インターフェイス)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
