---
title: "チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] ファイル名拡張子に新たなリンクのコンテンツの種類"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

独自のコンテンツの種類を定義し、エディター Managed Extensibility Framework \(MEF\) の拡張機能を使用して、ファイル名拡張子をリンクできます。 場合によっては、ファイル名拡張子既にによって定義されている言語のサービスです。それにもかかわらず、MEF で使用する必要がありますリンクさせる、コンテンツ タイプにします。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## MEF プロジェクトを作成します。  
  
1.  C\# の場合は、VSIX プロジェクトを作成します。 \(で、 **新しいプロジェクト** ダイアログで、 **Visual c\#\/機能拡張**, 、し **VSIX プロジェクト**.\) ソリューションの名前 `ContentTypeTest`します。  
  
2.  **Source.extension.vsixmanifest** に移動して、ファイル、 **資産** タブをクリックし、設定、 **型** フィールドを **\[microsoft.visualstudio.mefcomponent\]**, 、 **ソース** フィールドを **現在のソリューション内のプロジェクト**, 、および **プロジェクト** フィールドをプロジェクトの名前にします。  
  
## コンテンツの種類を定義します。  
  
1.  クラス ファイルを追加し、名前 `FileAndContentTypes`します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  次の追加 `using` ディレクティブです。  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  定義を格納する静的クラスを宣言します。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  このクラスでは、エクスポート、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> "hid"という名前を"text"を使用する基本定義を宣言します。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## ファイル名拡張子をコンテンツの種類にリンクします。  
  
-   ファイル名拡張子には、このコンテンツの種類をマップするには、エクスポート、 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ".hid"を拡張機能を持つし、コンテンツの種類"hid"です。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## エディターのエクスポートへのコンテンツの種類の追加  
  
1.  エディター拡張機能を作成します。 たとえば、」に記載の余白のグリフの拡張機能を使用することができます [チュートリアル: 余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)します。  
  
2.  この手順で定義したクラスを追加します。  
  
3.  拡張機能クラスをエクスポートする場合は、追加、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "\[NULL\] を非表示の種類のです。  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## 参照  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)