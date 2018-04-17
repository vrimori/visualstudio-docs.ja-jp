---
title: 言語の重要なコマンド サービス フィルター |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7affdbcad2b935a05420a2817c5d8bda5cd9cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="important-commands-for-language-service-filters"></a>言語サービスのフィルターの重要なコマンド
全機能を備えた言語サービスのフィルターを作成する場合は、次のコマンドの処理を検討してください。 コマンド識別子の完全な一覧が定義されている、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>アンマネージ列挙体のマネージ コードと Stdidcmd.h ヘッダー ファイル[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]コード。 Stdidcmd.h ファイルを検索する*Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc です。  
  
## <a name="commands-to-handle"></a>ハンドルするためのコマンド  
  
> [!NOTE]
>  次の表のすべてのコマンドをフィルター処理する必要はありません。  
  
|コマンド|説明|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーを右クリックしたときに送信します。 このコマンドは、ショートカット メニューを提供する時間であることを示します。 このコマンドを処理しない場合、テキスト エディターは、言語固有のコマンドとせず、既定のショートカット メニューを提供します。 このメニューでは、独自のコマンドを含めるには、コマンドを処理し、ショートカット メニューを表示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、ユーザーは、ctrl キーを押しながら J を入力したときに送信します。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ステートメント入力候補のボックスを表示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが入力文字と送信されます。 このコマンドは、トリガーの文字を入力し、ステートメントの提供を補完、メソッドのヒント、および構文の色分けなどのテキスト マーカー中かっこの照合、時期を決定しエラー マーカーを監視します。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>のステートメント入力候補、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>メソッド ヒントについてはします。 テキスト マーカーをサポートするには、型指定されている文字が、マーカーを更新することを必要とするかどうかを確認するには、このコマンドを監視します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが Enter キーを入力すると送信されます。 呼び出してメソッド ヒント ウィンドウを無視するかを判断するには、このコマンドを監視、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>です。 既定では、テキスト ビューは、このコマンドを処理します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーは、Backspace キーを入力すると送信されます。 呼び出してメソッド ヒント ウィンドウを無視するかを判断するモニター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>です。 既定では、テキスト ビューは、このコマンドを処理します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|メニューまたはショートカット キーから送信されます。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>とパラメーター情報、ヒント ウィンドウを更新します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが変数上に置いたまたは変数にカーソルを位置付けます選択して、送信される**クイック ヒント**から**IntelliSense**で、**編集**メニュー。 呼び出して、ヒントで変数の型を返す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。 デバッグが有効な場合は、ヒントはまた変数の値を表示する必要があります。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、ユーザーは、ctrl キーを押しながら space キーを入力したときに送信します。 このコマンドは、言語サービスを呼び出すを示します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、メニューから送信**選択範囲のコメント**または**選択範囲のコメントを解除**から**詳細**で、**編集**メニュー。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ユーザーが選択したテキストをコメントにすることを示します<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>ユーザーが選択されているテキストのコメントを解除することを示します。 これらのコマンドは、言語サービスによってのみ実装できます。|  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)