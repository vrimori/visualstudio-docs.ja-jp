---
title: 'チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3123624460066a70c35d988a0723c019516502ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926188"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>チュートリアル: コンテンツの種類をファイル名拡張子にリンクさせる
独自のコンテンツの種類を定義し、エディターの Managed Extensibility Framework (MEF) 拡張機能を使用して、ファイル名拡張子をリンクできます。 場合によっては、言語サービスで、ファイル名拡張子は既に定義されています。 しかし、MEF でこれを使用する必要がありますもをリンクするコンテンツの種類。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `ContentTypeTest`の名前を指定します。  
  
2.  **Source.extension.vsixmanifest**に移動して、ファイル、**資産**タブをクリックし、設定、**型**フィールドを **[microsoft.visualstudio.mefcomponent]**、**ソース**フィールドを**現在のソリューションでプロジェクトを**、および**プロジェクト**フィールドをプロジェクトの名前。  
  
## <a name="define-the-content-type"></a>コンテンツの種類を定義します。  
  
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
  
## <a name="link-a-file-name-extension-to-a-content-type"></a>コンテンツの種類に、ファイル名拡張子をリンクします。  
  
-   ファイル名拡張子には、このコンテンツの種類をマップするには、エクスポート、 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 、拡張機能を持つ *.hid*コンテンツの種類"hid"とします。  
  
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
  
## <a name="add-the-content-type-to-an-editor-export"></a>エディターとエクスポートをコンテンツ タイプを追加します。  
  
1.  エディター拡張機能を作成します。 たとえばで説明されている余白のグリフの拡張機能を使用することができます[チュートリアル。余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)です。  
  
2.  この手順で定義したクラスを追加します。  
  
3.  追加の拡張機能クラスをエクスポートするときに、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>に"hid"型の。  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)