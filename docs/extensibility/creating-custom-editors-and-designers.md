---
title: カスタム エディターとデザイナーを作成する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2c3f7a4b3f3219be4a4e3a40a0bb792b34599ce0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946998"
---
# <a name="create-custom-editors-and-designers"></a>カスタム エディターとデザイナーを作成します。
Visual Studio 統合開発環境 (IDE) では、さまざまな種類のエディターをホストできます。  
  
- Visual Studio のコア エディター  
  
- カスタム エディター  
  
- 外部エディター  
  
- デザイナー  
  
  次の情報を使用する必要があるエディターの種類を選択できます。  
  
## <a name="types-of-editor"></a>エディターの種類  
 Visual Studio のコア エディターについては、次を参照してください。[エディターと言語サービス拡張](../extensibility/extending-the-editor-and-language-services.md)します。  
  
### <a name="custom-editors"></a>カスタム エディター  
 カスタム エディターでは、特殊な状況で動作するように設計された 1 つです。 たとえばの機能は、Microsoft Exchange server などの特定のリポジトリにデータを読み書きするエディターを作成します。 プロジェクトの種類のみで動作するエディターまたは特定のいくつかのコマンドのみを持つエディターが必要な場合は、カスタム エディターを選択します。 ただし、ユーザーはいないできるカスタム エディターを使用して、標準を編集する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。  
  
 カスタム エディターは、エディター ファクトリを使用し、レジストリ エディターに関する情報を追加できます。 ただし、カスタム エディターに関連付けられているプロジェクトの種類には、他の方法でカスタム エディターがインスタンス化できます。  
  
 カスタム エディターは、インプレース アクティブ化または簡略化された埋め込みのいずれかを使用して、ビューを実装します。  
  
### <a name="external-editors"></a>外部エディター  
 外部エディターは、Microsoft Word、メモ帳や Microsoft FrontPage などの Visual Studio に統合されていないエディターです。 たとえば、テキストに渡すこと、VSPackage から場合は、このようなエディターを呼び出すことができます。 外部エディターでは、自身を登録し、Visual Studio 外部で使用することができます。 外部のエディターを呼び出すし、ホスト ウィンドウに埋め込むことが表示されます、IDE のウィンドウにします。 それ以外の場合は、そのし IDE が別のウィンドウを作成します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>メソッドを使用して、優先順位の設定、<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙体。 場合、`DP_External`値を指定すると、外部のエディターでファイルを開くことができます。  
  
## <a name="editor-design-decisions"></a>エディターの設計上の決定  
 次の設計に関する質問は、アプリケーションに最適な最適なエディターの種類を選択するのに役立ちます。  
  
- アプリケーション データが保存されますそのファイル内かどうか。 ファイル内のデータの保存は場合が、カスタムまたは標準の形式になりますか。  
  
   標準的なファイル形式を使用するだけでなく、プロジェクトの他のプロジェクトの種類を開き、読み取り/書き込みデータになります。 カスタム ファイル形式を使用する場合、プロジェクトの種類のみを開き、読み取り/書き込みデータになります。  
  
   プロジェクト ファイルを使用する場合は、標準のエディターをカスタマイズする必要があります。 プロジェクトでは、ファイルを使用しませんではなく、データベースまたはその他のリポジトリ内の項目を使用して、カスタム エディターを作成する必要があります。  
  
- エディターは、ActiveX コントロールをホストする必要がありますか。  
  
   エディターでは、ActiveX コントロールをホストしている場合、実装、インプレース アクティブ化エディター」の説明に従って[インプレース アクティブ化](../extensibility/in-place-activation.md)します。 ActiveX コントロールをホストしていない場合、またはいずれかを簡略化された埋め込みエディターを使用して、カスタマイズ、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]既定のエディター。  
  
- エディターは、複数のビューをサポートしますか。 既定のエディターと同時に表示される、エディターのビューの場合は、複数のビューをサポートする必要があります。  
  
   が複数のビューをサポートするために、エディターが必要な場合、ドキュメント データと、エディターのドキュメント ビュー オブジェクトは個別のオブジェクトになる可能性があります。 詳細については、次を参照してください。[ドキュメントの複数のビューをサポートして](../extensibility/supporting-multiple-document-views.md)します。  
  
   エディターでは、複数のビューをサポートする場合を使用して行う、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターのテキスト バッファーの実装 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクト)、ドキュメント データ オブジェクトのでしょうか。 エディター ビュー - サイドでをサポートする、つまり、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のコア エディターか? これを行う機能は、フォーム デザイナーの基になる.  
  
- 外部エディターをホストする必要がある場合、エディター内に埋め込むこと[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]でしょうか。  
  
   埋め込むことができる場合、外部のエディターのホスト ウィンドウを作成し、呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>メソッドとセット、<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙値を`DP_External`します。 エディターを埋め込むことができない、すると、別のウィンドウが自動的を作成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [チュートリアル: カスタム エディターを作成します。](../extensibility/walkthrough-creating-a-custom-editor.md)  
 カスタム エディターを作成する方法について説明します。  
  
 [チュートリアル: カスタム エディターに機能を追加します。](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 カスタム エディターに機能を追加する方法について説明します。  
  
 [デザイナーの初期化とメタデータの構成](../extensibility/designer-initialization-and-metadata-configuration.md)  
 デザイナーを初期化する方法について説明します。  
  
 [デザイナーに供給元に戻す機能](../extensibility/supplying-undo-support-to-designers.md)  
 デザイナーの取り消しのサポートを提供する方法について説明します。  
  
 [構文のカスタム エディターで色分け表示](../extensibility/syntax-coloring-in-custom-editors.md)  
 構文の色分けのコア エディターで、カスタム エディターでの違いについて説明します。  
  
 [ドキュメント データとカスタム エディターでドキュメント ビュー](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 カスタム エディターでドキュメント データとドキュメントのビューを実装する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [エディターでのレガシー インターフェイス](../extensibility/legacy-interfaces-in-the-editor.md)  
 従来の API を使用して、コア エディターにアクセスする方法について説明します。  
  
 [従来の言語サービスを開発します。](../extensibility/internals/developing-a-legacy-language-service.md)  
 言語サービスを実装する方法について説明します。  
  
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)  
 残りの部分に一致する UI 要素を作成する方法について説明します[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>