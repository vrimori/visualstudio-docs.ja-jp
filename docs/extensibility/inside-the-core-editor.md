---
title: コア エディター内で |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01756778c7937654339fe0fc41b752ed02659d3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828525"
---
# <a name="inside-the-core-editor"></a>コア エディター
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のコア エディターは変更し、テキスト情報のクエリを実行できるいくつかのコンポーネントのセットです。 従来の API を使用して、コア エディターをカスタマイズしている場合は、エディター アダプター経由でルーティングされますが、これらのカスタマイズを使用する続行することがあります。 お勧め、ただし、API の新しいエディターに、カスタマイズを調整することです。  
  
 コア エディターのいくつかの重要な側面を次の領域には。  
  
-   テキスト バッファー  
  
-   テキスト ビュー  
  
-   コード ウィンドウ  
  
-   テキスト マーカー  
  
-   テキスト マネージャー  
  
-   言語サービスとの統合  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 詳細な手順を使用する方法については、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>エディター、コアのインスタンスを作成します。  
  
 [従来の API を使用してテキスト バッファーへのアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 コア エディターでテキスト バッファーの役割について説明します、説明、バッファーにアクセスするために使用し、テキスト バッファー オブジェクトによって実装されるインターフェイスの一覧を提供する、関連付けられているシステム<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>します。  
  
 [従来の API でのテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 テキスト バッファー イベントの通知に使用されるインターフェイスの一覧を示します。  
  
 [方法: 従来の API を使用したイベントのテキスト バッファーの登録します。](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 テキスト バッファー イベントのことをお勧めする方法について説明します。  
  
 [テキスト マネージャーを使用して、グローバル設定を監視するには](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 コア エディター コンポーネントとグローバル設定情報を共有するテキスト マネージャーを使用する方法、およびテキスト マネージャー イベントの通知を受け取る方法について説明します。  
  
 [従来の API を使用してアクセス テキスト ビュー](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 コア エディターで、テキスト ビューの役割について説明し、によって実装されるインターフェイスを一覧表示、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>オブジェクト。  
  
 [従来の API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 コード ウィンドウによるテキスト ビューを囲むに使用する方法、コード ウィンドウ マネージャーを使用するコード ウィンドウで、文字装飾を提供する方法について説明する方法、および新しいビューの通知を提供します。 方法について説明します。  
  
 [従来の API を使用して、表示設定の変更](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 強制設定を削除する方法と設定の表示を強制する方法についての詳細な手順について説明します。  
  
 [言語サービスとコア エディター](../extensibility/language-services-and-the-core-editor.md)  
 制御コード文字装飾を言語サービスのインスタンス化について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [チュートリアル: コア エディターとエディター ファイルの種類の登録を作成します。](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 マネージ コードからのコア エディターを起動する方法についての詳細な手順について説明します。  
  
 [ドロップダウン バー](../extensibility/drop-down-bar.md)  
 ドロップダウン バーはコード ウィンドウで使用して、ドロップダウン バーを実装するときに使用するインターフェイスについて説明する方法について説明します。  
  
 [テキスト マーカーを使用して、従来の API を使用しました。](../extensibility/using-text-markers-with-the-legacy-api.md)  
 テキスト マーカーとそのコア エディターでの使用方法の概念について説明し、アクセスし、テキスト マーカーの管理に使用されるインターフェイスを一覧表示します。  
  
 [方法: 標準のテキスト マーカーを追加します。](../extensibility/how-to-add-standard-text-markers.md)  
 テキスト マーカーを作成する方法と、ショートカット メニューにカスタム コマンドを追加する方法に関する手順について説明します。  
  
 [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)  
 サービスとしてのマーカーの種類を指定する方法とカスタム テキスト マーカーを作成する方法の詳細手順について説明します。