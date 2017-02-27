---
title: "カスタム エディターとデザイナーを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デザイナー [Visual Studio SDK]"
  - "カスタム エディター [Visual Studio SDK]"
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# カスタム エディターとデザイナーを作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 統合開発環境 \(IDE\) では、さまざまな種類のエディターをホストできます。  
  
-   Visual Studio コア エディター  
  
-   カスタム エディター  
  
-   外部エディター  
  
-   デザイナー  
  
 次の情報を使用する必要がありますエディターの種類を選択できます。  
  
## エディターの種類  
 Visual Studio コア エディターの概要については、次を参照してください。 [エディターと言語サービスの拡張](../extensibility/extending-the-editor-and-language-services.md)します。  
  
##### カスタム エディター  
 カスタム エディターとは、特殊な状況で動作するよう設計です。 たとえば、関数がある Microsoft Exchange server などの特定のリポジトリにデータを読み書きするエディターを作成します。 プロジェクトの種類にのみで動作するエディターまたは特定のいくつかのコマンドのみを持つエディターが必要な場合の場合は、カスタム エディターを選択します。 ただし、ユーザーはいないできるカスタム エディターを使用して、標準の編集 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトです。  
  
 カスタム エディターでは、エディター ファクトリを使用でき、レジストリ エディターに関する情報を追加することができます。 ただし、カスタム エディターに関連付けられているプロジェクトの種類には、他の方法でカスタム エディターがインスタンス化できます。  
  
 カスタム エディターは、インプレース アクティブ化または簡略化された埋め込みのいずれかを使用して、ビューを実装します。  
  
##### 外部エディター  
 外部エディターは、Microsoft Word、メモ帳や Microsoft FrontPage などの Visual Studio に統合されていない編集者です。 などのテキストに渡すこと、VSPackage から場合は、このようなエディターを呼び出すことができます。 外部エディターでは、自身を登録し、Visual Studio の外部で使用することができます。 外部エディターを呼び出すし、ホスト ウィンドウに埋め込むことが可能が表示されます、IDE のウィンドウにします。 それ以外の場合は、IDE がそれに対応を別のウィンドウを作成し。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> メソッドを使用して、優先順位を設定する、 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 列挙します。 場合、 `DP_External` 値を指定すると、このファイルは外部エディターで開くことができます。  
  
## エディターのデザインの決定  
 次の設計に関する質問はアプリケーションに適して最適なエディターの種類を選択するのに役立ちます。  
  
-   アプリケーション データが保存されます、ファイル内かどうか。 場合はファイルには、そのデータを保存には、それが、カスタムまたは標準の形式で  
  
     標準的なファイル形式を使用するだけでなく、プロジェクトには、他のプロジェクト タイプを開いてを読み取り\/書き込みデータにすることになります。 カスタム ファイル形式を使用する場合、プロジェクトの種類のみを開くと読み取り\/書き込みデータになります。  
  
     プロジェクトでは、ファイルを使用する場合は、標準のエディターをカスタマイズする必要があります。 プロジェクトでは、ファイルを使用しませんではなく、データベースまたはその他のリポジトリ内の項目を使用して、カスタム エディターを作成する必要があります。  
  
-   エディターは、ActiveX コントロールをホストする必要があるでしょうか。  
  
     エディターでは、ActiveX コントロールをホストしている場合、エディターを実装する、インプレース アクティブ化、」の説明に従って [埋め込み先編集の有効化](../misc/in-place-activation.md)します。 ActiveX コントロールをホストしない場合、後簡略化された埋め込みエディターを使用するかをカスタマイズ、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 既定のエディターです。  
  
-   エディターは、複数のビューをサポートしますか。 既定のエディターと同時に表示される、エディターのビューの場合は、複数のビューをサポートする必要があります。  
  
     エディターは、複数のビューをサポートする必要がある場合、ドキュメント データと、エディターのドキュメント ビューのオブジェクトは個別のオブジェクトになる可能性があります。 詳細については、「[複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)」を参照してください。  
  
     エディターでは、複数のビューをサポートする場合は使用する場合、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エディターのテキスト バッファーの実装のコア \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> オブジェクト\) ドキュメントのデータ オブジェクトのでしょうか。 エディター ビュー サイド バイ サイドでをサポートする、つまり、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コア エディターですか? これを行う機能は、フォーム デザイナーの基になる.  
  
-   外部エディターをホストする必要がある場合、エディター内に埋め込むこと [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]でしょうか。  
  
     埋め込むことが可能である場合の外部エディター ホスト ウィンドウを作成し、まず、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> メソッドと、 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 列挙値を `DP_External`します。 エディターを埋め込むことができない、すると、別のウィンドウが自動的を作成します。  
  
## このセクションの内容  
 [チュートリアル: カスタム エディターの作成](../extensibility/walkthrough-creating-a-custom-editor.md)  
 カスタム エディターを作成する方法について説明します。  
  
 [チュートリアル: カスタム エディターの機能の追加](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 カスタム エディターに機能を追加する方法について説明します。  
  
 [デザイナーの初期化とメタデータの構成](../extensibility/designer-initialization-and-metadata-configuration.md)  
 デザイナーを初期化する方法について説明します。  
  
 [デザイナーに取り消しのサポートを提供します。](../extensibility/supplying-undo-support-to-designers.md)  
 デザイナーに取り消しのサポートを提供する方法について説明します。  
  
 [構文のカスタム エディターの色指定](../extensibility/syntax-coloring-in-custom-editors.md)  
 構文の色分けコア エディターおよびカスタム エディターの違いについて説明します。  
  
 [ドキュメント データとカスタム エディターでドキュメント ビュー](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 カスタム エディターでドキュメントのデータおよびドキュメントのビューを実装する方法について説明します。  
  
## 関連項目  
 [エディターでのレガシー インターフェイス](../extensibility/legacy-interfaces-in-the-editor.md)  
 従来の API を使用してコア エディターにアクセスする方法について説明します。  
  
 [言語サービスを開発します。](../extensibility/internals/developing-a-legacy-language-service.md)  
 言語サービスを実装する方法について説明します。  
  
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)  
 残りの部分に一致する UI 要素を作成する方法について説明 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>