---
title: "[プロパティ] ウィンドウからのフィールドの説明の取得 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[プロパティ] ウィンドウ、フィールドの説明"
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# [プロパティ] ウィンドウからのフィールドの説明の取得
**\[プロパティ\]** ウィンドウの下部にある説明領域に、選択したプロパティ フィールドに関連する情報が表示されます。 この機能は既定で有効になっています。 説明フィールドを非表示にするには、**\[プロパティ\]** ウィンドウを右クリックし、**\[説明\]** をクリックします。 これにより、メニュー ウィンドウの **\[説明\]** タイトルの横のチェック マークが削除されます。 同じ手順を行って **\[説明\]** の表示をオンに戻すことにより、フィールドを再度表示できます。  
  
 説明フィールド内の情報は <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> から取得されます。 それぞれのメソッド、インターフェイス、コクラスなどには、タイプ ライブラリのローカライズされていない `helpstring` 属性を適用できます。**\[プロパティ\]** ウィンドウは <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> から文字列を取得します。  
  
### ローカライズされたヘルプ文字列を指定するには  
  
1.  タイプ ライブラリ \(`typelib`\) のライブラリ ステートメントに `helpstringdll` 属性を追加します。  
  
    > [!NOTE]
    >  この手順は、タイプ ライブラリがオブジェクト ライブラリ \(.olb\) ファイルにある場合は省略可能です。  
  
2.  文字列の `helpstringcontext` 属性を指定します。`helpstring` 属性を指定することもできます。  
  
     これらの属性は、実際の.chm ファイルのヘルプ トピックに含まれる `helpfile` 属性と `helpcontext` 属性とは異なります。  
  
 強調表示されているプロパティ名に表示する説明情報を取得するために、**\[プロパティ\]** ウィンドウは選択したプロパティの <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> を呼び出し、出力文字列に対して目的の `lcid` 属性を指定します。 内部的には、<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> は `helpstringdll` 属性で指定された .dll ファイルを検索し、指定されたコンテキストと `lcid` 属性を使ってその .dll ファイル上に `DLLGetDocumentation` を呼び出します。  
  
 `DLLGetDocumentation` の署名と実装は次のとおりです。  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` 関数はDLL の .def ファイルで定義されているエクスポートである必要があります。  
  
 内部的には、実際には DLL である .olb ファイルが作成されます。 この DLL には、1 つのリソース、タイプ ライブラリ \(.tlb\) ファイル、および 1 つのエクスポートされた `DLLGetDocumentation` 関数が含まれます。  
  
 .olb ファイルの場合は、`helpstringdll` 属性は.tlb ファイル自体を含む同じファイルであるため省略可能です。  
  
 したがって、**\[説明\]** ウィンドウに表示する文字列を取得するために最低限必要な操作は、タイプ ライブラリに `helpstring` 属性を指定することです。 これらの文字列をローカライズする場合は、`helpstringdll` \(省略可能\) 属性と `helpstringcontext` \(必須\) 属性を指定し、`DLLGetDocumentation` を実装する必要があります  
  
 idl の `helpstringcontext` 属性と `DLLGetDocumentation` によって取得したローカライズされた情報を取得する場合は、実装する必要のある追加のインターフェイスはありません。  
  
 別の方法でプロパティのローカライズされた名前と説明の取得には、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> を実装します。 このメソッドの実装に関する詳細については、「[プロパティ ウィンドウのフィールドとインターフェイス](../extensibility/internals/properties-window-fields-and-interfaces.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [プロパティ ウィンドウのフィールドとインターフェイス](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [プロパティを拡張します。](../extensibility/internals/extending-properties.md)   
 [helpstringdll](/visual-cpp/windows/helpstringdll)   
 [helpstring](/visual-cpp/windows/helpstring)   
 [helpstringcontext](/visual-cpp/windows/helpstringcontext)   
 [helpcontext](/visual-cpp/windows/helpcontext)   
 [helpfile](/visual-cpp/windows/helpfile)   
 [lcid](/visual-cpp/windows/lcid)