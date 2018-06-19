---
title: カスタム エディターおよびデザイナーを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4c0dbc0db9d5116e372d96b43059a393ac8f4b5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105292"
---
# <a name="creating-custom-editors-and-designers"></a>カスタム エディターおよびデザイナーを作成します。
Visual Studio 統合開発環境 (IDE) では、さまざまな種類のエディターをホストできます。  
  
-   Visual Studio コア エディター  
  
-   カスタム エディター  
  
-   外部エディター  
  
-   デザイナー  
  
 次の情報を使用する必要がありますエディターの種類を選択できます。  
  
## <a name="types-of-editor"></a>エディターの種類  
 Visual Studio コア エディターの概要については、次を参照してください。[エディターと言語サービスの拡張](../extensibility/extending-the-editor-and-language-services.md)です。  
  
##### <a name="custom-editors"></a>カスタム エディター  
 カスタム エディターは、特殊な状況で動作するように設計されたものです。 たとえば、関数がある Microsoft Exchange server などの特定のリポジトリにデータを読み書きするエディターを作成する可能性があります。 場合、プロジェクトの種類のみで動作するエディターまたは特定のいくつかのコマンドのみを持つエディターをする場合は、カスタム エディターを選択します。 ただし、ユーザーがいないできるカスタム エディターを使用して標準を編集する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。  
  
 カスタム エディターでは、エディター ファクトリを使用でき、エディターに関する情報をレジストリに追加することができます。 ただし、カスタム エディターに関連付けられているプロジェクトの種類には、他の方法でカスタム エディターがインスタンス化できます。  
  
 カスタム エディターでは、ビューを実装する、インプレース アクティブ化または簡略化された埋め込みのいずれかを使用できます。  
  
##### <a name="external-editors"></a>外部エディター  
 外部のエディターは、Microsoft Word、メモ帳や Microsoft FrontPage などの Visual Studio に統合されていないエディターです。 たとえば、テキストを渡すこと、VSPackage から場合は、このようなエディターを呼び出す可能性があります。 外部エディターは、自身を登録し、Visual Studio の外部で使用することができます。 外部エディターを呼び出すし、ホスト ウィンドウに埋め込まれていることができます、し、表示され、IDE のウィンドウにします。 それ以外の場合は、IDE がその別のウィンドウを作成し。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>メソッドを使用して、優先順位の設定、<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙します。 場合、`DP_External`値を指定すると、外部エディターでファイルを開くことができます。  
  
## <a name="editor-design-decisions"></a>エディターの設計に関する決定事項  
 次の設計上の問題はアプリケーションに適してベスト エディターの種類を選択するのに役立ちます。  
  
-   アプリケーション データが保存されます、ファイル内かどうか。 ファイル内のデータが保存する場合、入手可能になります、カスタムまたは標準の形式にしますか。  
  
     標準ファイル形式を使用するプロジェクトだけでなく他のプロジェクトの種類を開き、読み取り/書き込みデータになります。 カスタム ファイル形式を使用する場合、プロジェクトの種類のみを開き、読み取り/書き込みデータになります。  
  
     プロジェクトでは、ファイルを使用する場合は、標準のエディターをカスタマイズする必要があります。 プロジェクトは、ファイルを使用しませんではなく、データベースまたはその他のリポジトリ内の項目を使用して、カスタム エディターを作成する必要があります。  
  
-   エディターは、ActiveX コントロールをホストする必要がありますか。  
  
     エディターでは、ActiveX コントロールをホストしている場合、実装、インプレース アクティブ化エディターで説明したよう[、インプレース アクティブ化](../extensibility/in-place-activation.md)です。 ActiveX コントロールをホストしない場合、またはいずれかを簡略化された埋め込みエディターを使用してカスタマイズ、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]既定のエディターです。  
  
-   エディターは、複数のビューをサポートしますか。 場合は、既定のエディターと同時に表示するエディターのビューには、複数のビューをサポートする必要があります。  
  
     エディターは、複数のビューをサポートする必要がある場合、ドキュメント データと、エディターのドキュメント ビュー オブジェクトは個別のオブジェクトになる可能性があります。 詳細については、次を参照してください。[複数ドキュメントのビューをサポートする](../extensibility/supporting-multiple-document-views.md)です。  
  
     エディターでは、複数のビューをサポートする場合は使用する場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターのテキスト バッファーの実装のコア (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクト)、ドキュメント データ オブジェクトのですか? する場合、エディター ビュー サイド バイ サイドでのサポート、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターしますか? これを行う機能は、フォーム デザイナーの基になる.  
  
-   外部エディターをホストする必要がある場合、エディター内に埋め込むこと[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]しますか?  
  
     埋め込むことができる場合、外部エディターをホスト ウィンドウを作成しを呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>メソッドとセット、<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列挙体の値`DP_External`です。 エディターを埋め込むことができない、すると、別のウィンドウが自動的を作成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [チュートリアル: カスタム エディターを作成する](../extensibility/walkthrough-creating-a-custom-editor.md)  
 カスタム エディターを作成する方法について説明します。  
  
 [チュートリアル: カスタム エディターに機能を追加する](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 カスタム エディターに機能を追加する方法について説明します。  
  
 [デザイナーの初期化とメタデータの構成](../extensibility/designer-initialization-and-metadata-configuration.md)  
 デザイナーを初期化する方法について説明します。  
  
 [デザイナー向けの元に戻す操作のサポート提供](../extensibility/supplying-undo-support-to-designers.md)  
 デザイナーの取り消しのサポートを提供する方法について説明します。  
  
 [カスタム エディターでの構文の色分け表示](../extensibility/syntax-coloring-in-custom-editors.md)  
 構文の色分けをコア エディターで、カスタム エディターでの違いについて説明します。  
  
 [カスタム エディターでのドキュメント データとドキュメント ビュー](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 カスタム エディターでドキュメントのデータおよびドキュメントのビューを実装する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [エディターでの従来のインターフェイス](../extensibility/legacy-interfaces-in-the-editor.md)  
 従来の API を使用して、コア エディターにアクセスする方法について説明します。  
  
 [従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)  
 言語サービスを実装する方法について説明します。  
  
 [Visual Studio の他の部分の拡張](../extensibility/extending-other-parts-of-visual-studio.md)  
 残りの部分に一致する UI 要素を作成する方法について説明[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>