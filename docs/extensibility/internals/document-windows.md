---
title: "ドキュメント ウィンドウ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK には、ドキュメント ウィンドウ"
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# ドキュメント ウィンドウ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio で、 *ドキュメント ウィンドウ* マルチ ドキュメント インターフェイス \(MDI\) ウィンドウに関連付けられているフレームを使用した子ウィンドウです。 ドキュメント ウィンドウは、通常、表示やソース コードまたはテキストの変更を使用しますが、他の機能の種類をホストすることもできます。 ドキュメント ウィンドウ:  
  
-   同時に複数のファイルを表示できるように、MDI 親の水平または垂直の別のタブ グループに整理できます。  
  
-   MDI 親の任意の順序でドッキングできます。  
  
-   自由にフロートすることができます。  
  
-   その他の MDI ウィンドウのタブ オーダー内でリンクされています。  
  
 グループ化のためのコマンドのフローティングとドッキング、ご覧 \[ウィンドウ\] タブのドキュメントのショートカット メニュー。  
  
 Visual Studio でウィンドウの動作の詳細については、次を参照してください。 [ウィンドウ レイアウトをカスタマイズする](../../ide/customizing-window-layouts-in-visual-studio.md)します。  
  
## ドキュメント ウィンドウの実装  
 ドキュメント ウィンドウを作成するには、エディターを実装します。<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> インターフェイスは、エディターのインスタンス化の一部としてドキュメント ウィンドウを作成します。 詳細については、「[エディターでのレガシー インターフェイス](../../extensibility/legacy-interfaces-in-the-editor.md)」を参照してください。  
  
> [!NOTE]
>  逆方向に提供をウィンドウのナビゲーションのポイントの転送は、実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> インターフェイスです。 テキスト エディターでは、ドキュメント内ナビゲーションのポイントを識別するためにテキストのマーカーが使用されます。  
  
## 実行中の Document テーブル  
 IDE では、実行中のドキュメント テーブル \(RDT\) を使用して、すべてのドキュメント ウィンドウの状態を追跡します。 RDT は、どのドキュメントを windows が、ソリューションを閉じたときなど、またはファイルを編集するときに、イベントの通知メカニズムです。 詳細については、「[実行中のドキュメント テーブル](../../extensibility/internals/running-document-table.md)」を参照してください。  
  
## 参照  
 [ドキュメントの読み込みの遅延](../../extensibility/internals/delayed-document-loading.md)