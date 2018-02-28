---
title: "ドキュメント ウィンドウ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 03e61b80aaf4c5c8b0e25f5b2a4a42f13d75d305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="document-windows"></a>ドキュメント ウィンドウ
Visual Studio で、*ドキュメント ウィンドウ*マルチ ドキュメント インターフェイス (MDI) ウィンドウに関連付けられているフレームを使用した子ウィンドウします。 ドキュメント ウィンドウは、通常、ディスプレイとソース コードまたはテキストの変更の使用が、他の機能の種類をホストすることもできます。 ドキュメント ウィンドウ:  
  
-   同時に複数のファイルを表示できるように、MDI 親の別個の水平または垂直タブ グループに編成できます。  
  
-   MDI 親の任意の順序でドッキングできます。  
  
-   自由にフロートことができます。  
  
-   その他の MDI ウィンドウのタブ オーダー内でリンクされています。  
  
 グループ化のため、コマンド、ドッキングとフローティングにありますドキュメント ウィンドウ タブのショートカット メニュー。  
  
 Visual Studio でのウィンドウの動作の詳細については、次を参照してください。[ウィンドウ レイアウトをカスタマイズする](../../ide/customizing-window-layouts-in-visual-studio.md)です。  
  
## <a name="document-window-implementation"></a>ドキュメント ウィンドウの実装  
 ドキュメント ウィンドウは、エディターの実装によって作成されます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイスは、エディターのインスタンス化の一部としてドキュメント ウィンドウを作成します。 詳細については、次を参照してください。[エディターでのレガシ インターフェイス](../../extensibility/legacy-interfaces-in-the-editor.md)です。  
  
> [!NOTE]
>  逆方向に提供し、ウィンドウのナビゲーション指し示す前方、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>インターフェイスです。 テキスト エディターでは、ドキュメント内のナビゲーションの点を識別するのにテキスト マーカーが使用されます。  
  
## <a name="the-running-document-table"></a>実行中のドキュメント テーブル  
 IDE では、すべてのドキュメント ウィンドウのステータスを追跡するために実行中のドキュメント テーブル (RDT) を使用します。 RDT は、どのドキュメントを windows にソリューションが閉じている場合など、または、ファイルが編集されているときに、イベントの通知メカニズムです。 詳細については、次を参照してください。[を実行しているドキュメント テーブル](../../extensibility/internals/running-document-table.md)です。  
  
## <a name="see-also"></a>参照  
 [ドキュメントの読み込みの遅延](../../extensibility/internals/delayed-document-loading.md)