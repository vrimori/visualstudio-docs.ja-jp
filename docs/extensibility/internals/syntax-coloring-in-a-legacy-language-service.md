---
title: "構文の色分けで従来の言語サービス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "構文の色指定"
  - "言語サービスでは、構文の色分け表示"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 構文の色分けで従来の言語サービス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は言語要素を特定しエディターで指定された色で表示の色指定にサービスを使用します。  
  
## Colorizer モデル  
 言語サービスはエディターによって使用される <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> のインターフェイスを実装します。  この実装では次の図に示すように言語サービスの各オブジェクトです。  
  
 ![SVC Colorizer グラフィック](../../extensibility/internals/media/figlgsvccolorizer.png "FigLgSvcColorizer")  
単純なモデル colorizer  
  
> [!NOTE]
>  構文の色指定サービスは colorizing テキストの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 一般機能とは異なります。  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 一般機能をサポートして colorizing する方法の詳細については[フォントおよび色を使用します。](../../extensibility/using-fonts-and-colors.md) を参照してください。  
  
 colorizer だけでなく言語サービスは指定したカスタム色設定可能項目を指定したエディターで使用されるカスタム色設定可能項目を指定できます。  同じオブジェクトの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> インターフェイスの実装によって実装するインターフェイスの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 行うことができます。  これはエディターが <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> のメソッドを呼び出すとエディターが <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> のメソッドを呼び出して個々のカスタム色設定可能項目を返すときにカスタム色設定可能項目数を返します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> のメソッドを実装するオブジェクト <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> のインターフェイス。  言語サービスのサポートで表現またはハイ カラー値では<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> のインターフェイスと同じオブジェクトの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> のインターフェイスを実装する必要があります。  
  
## VSPackage が Colorizer 言語サービスを使用する方法  
  
1.  VSPackage は言語サービスはVSPackage を実行するように要求する適切な言語サービスを取得する必要があります :  
  
    1.  テキストを colorized するには <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> のインターフェイスを実装するオブジェクトを使用します。  
  
         テキストはオブジェクトを使用してを実装するインターフェイスの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 表示されます。  
  
    2.  言語サービスの GUID の VSPackage サービス プロバイダーを利用して言語サービスを取得します。  言語サービスは拡張子によってレジストリで識別されます。  
  
    3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> のメソッドを呼び出して <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> と言語サービスを関連付けます。  
  
2.  VSPackage は次のようにcolorizer オブジェクトを取得し使用する :  
  
    > [!NOTE]
    >  VSPackage はコア エディターを使用する言語サービスの colorizer のオブジェクトを明示的に取得する必要はありません。  コア エディターのインスタンスが適切な言語サービスを取得すると次に示すすべての色づけのタスクを実行します。  
  
    1.  `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` を実行すると<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> のインターフェイスを取得します <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 言語サービスのオブジェクトの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> のメソッドを呼び出して言語サービスの colorizer のオブジェクト。  
  
    2.  テキストの特定の範囲の colorizer 情報を取得するために <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> のメソッドを呼び出します。  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 値はcolorized テキスト範囲内の各文字に 1 の配列を返します。  値はコア エディターで保持される既定の色設定可能項目の一覧または言語サービス自体を保持するカスタム色設定可能項目リストの色設定可能項目の一覧へのインデックスです。  
  
    3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> のメソッドによって返される情報選択したテキストの表示に色づけを使用します。  
  
> [!NOTE]
>  言語サービスの colorizer に加えてVSPackage は汎用の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のテキストの色指定機能を使用できます。  この機能の詳細については[フォントおよび色を使用します。](../../extensibility/using-fonts-and-colors.md) を参照してください。  
  
## このセクションの内容  
 [構文の色分けを実装します。](../../extensibility/internals/implementing-syntax-coloring.md)  
 エディターで言語サービスの構文の色指定にアクセスしますが構文の色指定をサポートする言語サービスが実行する方法について説明します。  
  
 [方法: ビルトインの装飾が可能な項目を使用して](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 言語サービスの組み込みの色設定可能項目を使用する方法を示します。  
  
 [カスタムの装飾が可能な項目](../../extensibility/internals/custom-colorable-items.md)  
 カスタム色設定可能項目を実装する方法について説明します。  
  
## 参照  
 [フォントおよび色を使用します。](../../extensibility/using-fonts-and-colors.md)