---
title: "コア エディター内 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4612f5779d6177d58cef7f087ef6e11bbe4ebd9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-core-editor"></a>コア エディター内
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターには、一連のいくつかのコンポーネントを変更し、テキストの情報を照会できます。 レガシ API を使用して、コア エディターをカスタマイズした場合は、エディター アダプター経由でルーティングされますが、これらのカスタマイズを使用する続行することがあります。 お勧め、ただし、API の新しいエディターに、カスタマイズを調整することです。  
  
 コア エディターのいくつかの重要な側面を次の領域には。  
  
-   テキスト バッファー  
  
-   テキスト ビュー  
  
-   コード ウィンドウ  
  
-   テキスト マーカー  
  
-   テキスト マネージャー  
  
-   言語サービスとの統合  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レガシ API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 使用方法に関する手順をわかりやすく説明<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>エディターのコアのインスタンスを作成します。  
  
 [レガシ API を使用してテキスト バッファーにアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 コア エディターでテキスト バッファーの役割について説明します、説明、バッファーにアクセスするために使用し、テキスト バッファー オブジェクトによって実装されるインターフェイスの一覧を提供する関連システム<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>です。  
  
 [レガシ API でのテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 テキスト バッファー イベントの通知に使用されるインターフェイスのリストを提供します。  
  
 [方法: テキスト バッファー イベント、レガシ API の登録](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 テキスト バッファーのイベントを通知する方法について説明します。  
  
 [テキスト マネージャーを使用して、グローバル設定を監視するには](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 コア エディターのコンポーネントとグローバル設定情報を共有するテキスト マネージャーを使用する方法、およびテキスト マネージャー イベントの通知を受信する方法について説明します。  
  
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 コア エディターでテキスト ビューの役割について説明し、によって実装されるインターフェイスを一覧表示、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>オブジェクト。  
  
 [レガシ API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 方法、コード ウィンドウ テキスト ビューを囲むために使用がコード ウィンドウ マネージャーを使用してコード ウィンドウに装飾を提供する方法について説明し、新しいビューの通知に関する情報を提供します。  
  
 [レガシ API を使用してビューの設定を変更します。](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 強制設定を削除する方法と設定の表示を強制する方法に関する詳細な手順を説明します。  
  
 [言語サービスとコア エディター](../extensibility/language-services-and-the-core-editor.md)  
 制御コード文字装飾を言語サービスのインスタンス化について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録します。](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 マネージ コードからコア エディターを起動する方法について詳細な手順を説明します。  
  
 [ドロップダウン バー](../extensibility/drop-down-bar.md)  
 ドロップダウン バーのコード ウィンドウで使用され、ドロップダウン バーを実装するときに使用されるインターフェイスの説明について説明します。  
  
 [レガシ API でテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)  
 テキスト マーカーとコア エディターの使用方法の概念について説明し、アクセスし、テキストのマーカーの管理に使用されるインターフェイスを一覧表示します。  
  
 [方法: 標準のテキストのマーカーの追加](../extensibility/how-to-add-standard-text-markers.md)  
 テキスト マーカーを作成する方法と、ショートカット メニューにカスタム コマンドを追加する方法に関する詳細な手順を説明します。  
  
 [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)  
 操作手順については、マーカーの種類のサービスとして提供する方法とカスタム テキスト マーカーを作成する方法を提供します。