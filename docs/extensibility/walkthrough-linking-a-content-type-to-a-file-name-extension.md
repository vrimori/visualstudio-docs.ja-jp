---
title: 'チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54570ec03788f88f58f14249f200ed2028686c37
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566754"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>チュートリアル: コンテンツの種類をファイル名拡張子にリンクします。
独自のコンテンツの種類を定義し、エディターの Managed Extensibility Framework (MEF) 拡張機能を使用して、ファイル名拡張子をリンクできます。 場合によっては、言語サービスで、ファイル名拡張子は既に定義されています。 しかし、MEF でこれを使用する必要がありますもをリンクするコンテンツの種類。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="create-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を`ContentTypeTest`します。  
  
2.  **Source.extension.vsixmanifest**に移動して、ファイル、**資産**タブをクリックし、設定、**型**フィールドを **[microsoft.visualstudio.mefcomponent]**、**ソース**フィールドを**現在のソリューションでプロジェクトを**、および**プロジェクト**フィールドをプロジェクトの名前。  
  
## <a name="define-the-content-type"></a>コンテンツの種類を定義します。  
  
1.  クラス ファイルを追加し、名前`FileAndContentTypes`します。  
  
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
  
1.  エディター拡張機能を作成します。 たとえばで説明されている余白のグリフの拡張機能を使用することができます[チュートリアル: 余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)です。  
  
2.  この手順で定義したクラスを追加します。  
  
3.  追加の拡張機能クラスをエクスポートするときに、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>に"hid"型の。  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)