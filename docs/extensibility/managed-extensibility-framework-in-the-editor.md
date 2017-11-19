---
title: "Managed Extensibility Framework エディターで |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4677b10d54a6c591c2f60e4c0b1f2978ad49a0ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="managed-extensibility-framework-in-the-editor"></a>エディターでの managed Extensibility Framework
エディターは、Managed Extensibility Framework (MEF) コンポーネントを使用して作成されています。 エディターを拡張する独自の MEF コンポーネントをビルドして、コード エディターのコンポーネントもを使用できます。  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework の概要  
 MEF は、追加し、アプリケーションまたはプログラミング モデルに MEF コンポーネントの機能の変更できる .NET ライブラリです。 Visual Studio エディターは、ことができます両方を提供し、MEF コンポーネント パーツを使用します。  
  
 MEF は、.NET Framework version 4 System.ComponentModel.Composition.dll アセンブリに含まれます。  
  
 MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)です。  
  
### <a name="component-parts-and-composition-containers"></a>コンポーネントのパートと合成コンテナー  
 コンポーネントの一部は、クラス、または、次のいずれか (または両方) を実行できるクラスのメンバーには。  
  
-   別のコンポーネントを使用します。  
  
-   別のコンポーネントで利用できます。  
  
 たとえば、倉庫在庫コンポーネントによって提供される製品の可用性データに依存する注文エントリ コンポーネントのあるショッピング アプリケーションがあるとします。 在庫部品ができる MEF の用語で*エクスポート*製品の可用性データ、および、注文エントリの一部は*インポート*データ。 注文エントリ部分と在庫部分は; 相互について知ることはありません。*合成コンテナー* (ホスト アプリケーションによって提供される) は、エクスポートのセットを管理して、エクスポートの解決を担当し、インポートします。  
  
 合成コンテナー<xref:System.ComponentModel.Composition.Hosting.CompositionContainer>は、通常、ホストによって所有されます。 合成コンテナーを保持する*カタログ*エクスポートされた構成部品のです。  
  
### <a name="exporting-and-importing-component-parts"></a>エクスポートとインポート構成部品  
 パブリック クラスまたはクラス (プロパティまたはメソッド) のパブリック メンバーとして実装されている限り、任意の機能をエクスポートできます。 コンポーネント部分を派生する必要はありません<xref:System.ComponentModel.Composition.Primitives.ComposablePart>です。 代わりに、追加する必要があります、<xref:System.ComponentModel.Composition.ExportAttribute>属性をクラスまたはクラス メンバーをエクスポートします。 この属性を指定、*コントラクト*パーツを別のコンポーネント、機能をインポートできます。  
  
### <a name="the-export-contract"></a>エクスポートのコントラクト  
 <xref:System.ComponentModel.Composition.ExportAttribute>エクスポートされるエンティティ (クラス、インターフェイス、または構造体) を定義します。 通常、エクスポート属性は、エクスポートの種類を指定するパラメーターを受け取ります。  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 既定では、<xref:System.ComponentModel.Composition.ExportAttribute>属性は、エクスポート クラスの型であるコントラクトを定義します。  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 例では、既定値`[Export]`属性は等価`[Export(typeof(TestAdornmentLayerDefinition))]`です。  
  
 次の例で示すように、またプロパティまたはメソッドをエクスポートすることができます。  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>MEF エクスポートをインポートします。  
 MEF エクスポートを使用する場合は、(通常は型) に、エクスポートされたし、使用する追加のコントラクトを知る必要があります、<xref:System.ComponentModel.Composition.ImportAttribute>をその値を持つ属性。 既定では、このインポート属性がそれを変更するクラスの型は、1 つのパラメーターを受け取る。 次のコードのインポートの行、<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>型です。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>MEF コンポーネント パーツからエディターの機能を取得します。  
 既存のコードに MEF コンポーネント パーツがある場合は、エディターのコンポーネント部分を使用する MEF メタデータを使用できます。  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>MEF コンポーネント パーツからエディター機能を使用するには  
  
1.  グローバル アセンブリ キャッシュ (GAC) にある System.Composition.ComponentModel.dll してエディターのアセンブリ参照を追加します。  
  
2.  関連する追加のステートメントを使用します。  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  追加、`[Import]`属性をサービス インターフェイスの次のようにします。  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  サービスを取得したときに、そのコンポーネントのいずれかを利用できます。  
  
5.  独自のアセンブリをコンパイルしたときに、.Visual Studio のインストールの \Common7\IDE\Components\ フォルダーです。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)