---
title: "Managed Extensibility Framework、エディターで |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
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
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>エディターで managed Extensibility Framework
エディターは、Managed Extensibility Framework (MEF) コンポーネントを使用して構築されます。 エディターを拡張する、独自の MEF コンポーネントをビルドして、コードがエディターのコンポーネントもを使用することができます。  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework の概要  
 MEF は、.NET ライブラリを追加し、アプリケーションまたはプログラミング モデルに MEF コンポーネントの機能を変更できます。 Visual Studio エディターは、提供両方と MEF コンポーネントのパートを使用します。  
  
 MEF は、.NET Framework version 4 System.ComponentModel.Composition.dll アセンブリに含まれます。  
  
 MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)します。  
  
### <a name="component-parts-and-composition-containers"></a>コンポーネントのパートと合成コンテナー  
 コンポーネントの一部は、クラス、または、次のいずれか (または両方) を実行できるクラスのメンバーには。  
  
-   別のコンポーネントを使用します。  
  
-   別のコンポーネントで使用できます。  
  
 たとえば、倉庫の在庫コンポーネントによって提供される製品の可用性データに依存する注文エントリ コンポーネントのあるショッピング アプリケーションがあるとします。 在庫部品をできる MEF の用語で*エクスポート*製品可用性データと注文エントリの一部が*インポート*データ。 注文入力部分と在庫部品する必要はありません。 は次のトピック*合成コンテナー* (ホスト アプリケーションによって提供される) は、エクスポートのセットを管理して、エクスポートの解決を行うと、インポートします。  
  
 合成コンテナー<xref:System.ComponentModel.Composition.Hosting.CompositionContainer>が、通常、ホストによって所有されている</xref:System.ComponentModel.Composition.Hosting.CompositionContainer>。 合成コンテナーを維持、*カタログ*エクスポートされた構成部品のです。  
  
### <a name="exporting-and-importing-component-parts"></a>エクスポートとインポート構成部品  
 パブリック クラスまたはクラス (プロパティまたはメソッド) のパブリック メンバーとして実装されている限り、すべての機能をエクスポートできます。 構成部品を<xref:System.ComponentModel.Composition.Primitives.ComposablePart>。</xref:System.ComponentModel.Composition.Primitives.ComposablePart>から派生する必要はありません。 代わりに、追加する必要があります、<xref:System.ComponentModel.Composition.ExportAttribute>属性をクラスまたはクラス メンバーをエクスポートする</xref:System.ComponentModel.Composition.ExportAttribute>。 この属性を指定、*コントラクト*する別のコンポーネントで、一部が、機能をインポートできます。  
  
### <a name="the-export-contract"></a>エクスポートのコントラクト  
 <xref:System.ComponentModel.Composition.ExportAttribute>エクスポートされる (クラス、インターフェイス、または構造体) のエンティティを定義します</xref:System.ComponentModel.Composition.ExportAttribute>。 通常、エクスポート属性は、エクスポートの型を指定するパラメーターを受け取ります。  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 既定では、<xref:System.ComponentModel.Composition.ExportAttribute>属性は、エクスポート側のクラス型では、コントラクトを定義します。</xref:System.ComponentModel.Composition.ExportAttribute>  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 例では、既定値で`[Export]`属性は`[Export(typeof(TestAdornmentLayerDefinition))]`です。  
  
 次の例で示すように、また、プロパティまたはメソッドをエクスポートすることができます。  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>MEF エクスポートをインポートします。  
 MEF エクスポートを使用する場合は、(通常は型) で、エクスポートされた、追加のコントラクトを知る必要があります、<xref:System.ComponentModel.Composition.ImportAttribute>をその値を持つ属性です</xref:System.ComponentModel.Composition.ImportAttribute>。 既定は、インポート属性は、それを変更するクラスの型である&1; つのパラメーターを受け取ります。 次の行のコードのインポート、<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>型です</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>MEF コンポーネント パーツからエディター機能の取得  
 MEF コンポーネントの一部の場合は、既存のコードは、コンポーネント部分のエディターを使用する MEF メタデータを使用できます。  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>MEF コンポーネント パーツからエディターの機能を使用するには  
  
1.  グローバル アセンブリ キャッシュ (GAC) にある System.Composition.ComponentModel.dll にし、エディターのアセンブリへの参照を追加します。  
  
2.  関連する追加のステートメントを使用します。  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  追加、`[Import]`属性、サービス インターフェイスを次のようにします。  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  サービスを入手した場合は、そのコンポーネントのいずれかを利用できます。  
  
5.  独自のアセンブリがコンパイルされると、.Visual Studio のインストールの \Common7\IDE\Components\ フォルダーです。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)
