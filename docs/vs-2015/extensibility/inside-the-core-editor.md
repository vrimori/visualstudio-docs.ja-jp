---
title: コア エディター内で |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc91a228fd788074a543678b281288e043f9385c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227735"
---
# <a name="inside-the-core-editor"></a>コア エディター内で
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]のコア エディターは変更し、テキスト情報のクエリを実行できるいくつかのコンポーネントのセットです。 従来の API を使用して、コア エディターをカスタマイズしている場合は、エディター アダプター経由でルーティングされますが、これらのカスタマイズを使用する続行することがあります。 お勧め、ただし、API の新しいエディターに、カスタマイズを調整することです。  
  
 コア エディターのいくつかの重要な側面を次の領域には。  
  
-   テキスト バッファー  
  
-   テキスト ビュー  
  
-   コード ウィンドウ  
  
-   テキスト マーカー  
  
-   テキスト マネージャー  
  
-   言語サービスとの統合  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レガシ API を使用するコア エディターのインスタンス化](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 詳細な手順を使用する方法については、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>エディター、コアのインスタンスを作成します。  
  
 [レガシ API を使用するテキスト バッファーへのアクセス](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 コア エディターでテキスト バッファーの役割について説明します、説明、バッファーにアクセスするために使用し、テキスト バッファー オブジェクトによって実装されるインターフェイスの一覧を提供する、関連付けられているシステム<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>します。  
  
 [レガシ API のテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 テキスト バッファー イベントの通知に使用されるインターフェイスの一覧を示します。  
  
 [方法: レガシ API でテキスト バッファー イベントを登録する](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 テキスト バッファー イベントのことをお勧めする方法について説明します。  
  
 [グローバル設定を監視するためのテキスト マネージャーの使用](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 コア エディター コンポーネントとグローバル設定情報を共有するテキスト マネージャーを使用する方法、およびテキスト マネージャー イベントの通知を受け取る方法について説明します。  
  
 [レガシ API を使用するテキスト ビューへのアクセス](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 コア エディターで、テキスト ビューの役割について説明し、によって実装されるインターフェイスを一覧表示、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>オブジェクト。  
  
 [レガシ API を使用するコード ウィンドウのカスタマイズ](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 コード ウィンドウによるテキスト ビューを囲むに使用する方法、コード ウィンドウ マネージャーを使用するコード ウィンドウで、文字装飾を提供する方法について説明する方法、および新しいビューの通知を提供します。 方法について説明します。  
  
 [レガシ API を使用する表示設定の変更](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 強制設定を削除する方法と設定の表示を強制する方法についての詳細な手順について説明します。  
  
 [言語サービスとコア エディター](../extensibility/language-services-and-the-core-editor.md)  
 制御コード文字装飾を言語サービスのインスタンス化について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [チュートリアル: コア エディターの作成とエディター ファイルの種類の登録](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 マネージ コードからのコア エディターを起動する方法についての詳細な手順について説明します。  
  
 [ドロップダウン バー](../extensibility/drop-down-bar.md)  
 ドロップダウン バーはコード ウィンドウで使用して、ドロップダウン バーを実装するときに使用するインターフェイスについて説明する方法について説明します。  
  
 [レガシ API でのテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)  
 テキスト マーカーとそのコア エディターでの使用方法の概念について説明し、アクセスし、テキスト マーカーの管理に使用されるインターフェイスを一覧表示します。  
  
 [方法: 標準のテキスト マーカーを追加する](../extensibility/how-to-add-standard-text-markers.md)  
 テキスト マーカーを作成する方法と、ショートカット メニューにカスタム コマンドを追加する方法に関する手順について説明します。  
  
 [方法: カスタム テキスト マーカーを作成する](../extensibility/how-to-create-custom-text-markers.md)  
 サービスとしてのマーカーの種類を指定する方法とカスタム テキスト マーカーを作成する方法の詳細手順について説明します。

