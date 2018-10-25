---
title: Managed Extensibility Framework、エディターで |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5ea47032ed2c5e4fb9b99afb214e068ca39d692
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857524"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>エディターでの managed Extensibility Framework
エディターは、Managed Extensibility Framework (MEF) コンポーネントを使用して構築されます。 エディターを拡張する、独自の MEF コンポーネントをビルドして、コード エディターのコンポーネントもを使用できます。  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework の概要  
 MEF では、.NET ライブラリを追加し、アプリケーションや、MEF プログラミング モデルを次のコンポーネントの機能を変更することができます。 Visual Studio エディターでは、ことができます、提供および両方 MEF コンポーネント パーツを使用します。  
  
 MEF が .NET Framework version 4 に含まれている*System.ComponentModel.Composition.dll*アセンブリ。  
  
 MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)します。  
  
### <a name="component-parts-and-composition-containers"></a>コンポーネントの部分と合成コンテナー  
 コンポーネントの一部は、クラス、または、次のいずれか (または両方) を実行できるクラスのメンバーには。  
  
- 別のコンポーネントを使用します。  
  
- 別のコンポーネントで消費されます。  
  
  たとえば、倉庫の在庫コンポーネントによって提供される製品の可用性データに依存する注文エントリ コンポーネントを含むショッピング アプリケーションを検討してください。 在庫部品をできる MEF の用語で*エクスポート*製品の可用性データ、および注文のエントリに、一部は*インポート*データ。 注文の入力部分とインベントリの一部が; 相互について知っておく必要は*合成コンテナー* (ホスト アプリケーションによって提供される) のエクスポート、セットを維持し、エクスポートの解決を担当してインポートします。  
  
  合成コンテナー、<xref:System.ComponentModel.Composition.Hosting.CompositionContainer>は、通常、ホストによって所有されます。 合成コンテナーを保持する*カタログ*エクスポートされた構成部品の。  
  
### <a name="export-and-import-component-parts"></a>エクスポートおよびインポート コンポーネント パーツ  
 パブリック クラスまたはクラス (プロパティまたはメソッド) のパブリック メンバーとして実装されます限り、機能をエクスポートできます。 コンポーネント部分を派生する必要はありません<xref:System.ComponentModel.Composition.Primitives.ComposablePart>します。 代わりに、追加する必要があります、<xref:System.ComponentModel.Composition.ExportAttribute>属性をクラスまたはクラス メンバーをエクスポートします。 この属性を指定します、*コントラクト*一部を別のコンポーネントで、機能をインポートできます。  
  
### <a name="the-export-contract"></a>エクスポートのコントラクト  
 <xref:System.ComponentModel.Composition.ExportAttribute>エクスポートされるエンティティ (クラス、インターフェイス、または構造体) を定義します。 通常、エクスポート属性は、エクスポートの種類を指定するパラメーターを受け取ります。  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 既定で、<xref:System.ComponentModel.Composition.ExportAttribute>属性は、エクスポート クラスの型であるコントラクトを定義します。  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 例では、既定で`[Export]`属性は等価`[Export(typeof(TestAdornmentLayerDefinition))]`します。  
  
 次の例に示すようにも、プロパティまたはメソッドをエクスポートできます。  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="import-a-mef-export"></a>インポートと MEF エクスポート  
 MEF エクスポートを使用する場合は、(通常は型) で、エクスポートされた、追加のコントラクトを知る必要があります、<xref:System.ComponentModel.Composition.ImportAttribute>をその値を持つ属性です。 既定は、インポート属性は、それを変更するクラスの型は、1 つのパラメーターを移動します。 次の行のコードのインポート、<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>型。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="get-editor-functionality-from-a-mef-component-part"></a>MEF コンポーネント パーツからエディター機能を取得します。  
 既存のコードが、MEF コンポーネント パーツの場合は、エディター コンポーネント パーツを使用する MEF メタデータを使用できます。  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>MEF コンポーネント パーツからエディター機能を使用するには  
  
1.  参照を追加*System.Composition.ComponentModel.dll*は、エディターのアセンブリをグローバル アセンブリ キャッシュ (GAC) にします。  
  
2.  関連する追加ステートメントを使用します。  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  追加、`[Import]`属性、サービス インターフェイスを次のようにします。  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  サービスを入手した場合は、ときに、そのコンポーネントのいずれかを使用できます。  
  
5.  独自のアセンブリをコンパイルしたときに、*.\Common7\IDE\Components\* Visual Studio のインストールのフォルダー。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)