---
title: 'チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45534f4a85cd289360c098083228ac5f28025a90
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261730"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

独自のコンテンツの種類を定義し、エディターの Managed Extensibility Framework (MEF) 拡張機能を使用して、ファイル名拡張子をリンクできます。 場合によっては、ファイル名拡張子が言語サービスでは; で定義されて既にそれにもかかわらず、MEF を使用してもする必要がありますをリンクするコンテンツの種類。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `ContentTypeTest`の名前を指定します。  
  
2.  **Source.extension.vsixmanifest**に移動して、ファイル、**資産**タブをクリックし、設定、**型**フィールドを **[microsoft.visualstudio.mefcomponent]**、**ソース**フィールドを**現在のソリューションでプロジェクトを**、および**プロジェクト**フィールドをプロジェクトの名前。  
  
## <a name="defining-the-content-type"></a>コンテンツの種類を定義します。  
  
1.  クラス ファイルを追加し、その名前を `FileAndContentTypes`にします。  
  
2.  次のアセンブリへの参照を追加します。  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  次の追加`using`ディレクティブ。  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  定義を含む静的クラスを宣言します。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  このクラスは、エクスポート、<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>という名前の「非表示」と"text"をその基本定義を宣言します。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>コンテンツの種類に、ファイル名拡張子をリンク  
  
-   ファイル名拡張子には、このコンテンツの種類をマップするには、エクスポート、 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ".hid"を拡張機能を持つし、コンテンツの種類"hid"。  
  
    ```csharp  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>エディターのエクスポートへのコンテンツの種類の追加  
  
1.  エディター拡張機能を作成します。 たとえばで説明されている余白のグリフの拡張機能を使用することができます[チュートリアル: 余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)です。  
  
2.  この手順で定義したクラスを追加します。  
  
3.  追加の拡張機能クラスをエクスポートするときに、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>に"hid"型の。  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)

