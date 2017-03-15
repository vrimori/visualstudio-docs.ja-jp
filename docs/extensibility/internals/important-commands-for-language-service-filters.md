---
title: "重要なコマンド言語のフィルターのサービス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6b5bad11c47074c29f3b319678419f1e42ab91b
ms.lasthandoff: 02/22/2017

---
# <a name="important-commands-for-language-service-filters"></a>言語サービスのフィルターの重要なコマンド
機能を備えた完全言語サービス フィルターを作成する場合は、次のコマンドの処理を検討してください。 コマンド識別子の完全な一覧が定義されている、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>アンマネージ列挙体のマネージ コードと Stdidcmd.h ヘッダー ファイル[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]コード</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>。 Stdidcmd.h ファイルを検索する*Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc します。  
  
## <a name="commands-to-handle"></a>ハンドルするためのコマンド  
  
> [!NOTE]
>  場合によっては、すべてのコマンドは、次の表のフィルター処理する必要はありません。  
  
|コマンド|説明|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーを右クリックしたときに送信されます。 このコマンドは、ショートカット メニューを提供する時間であることを示します。 このコマンドを処理しない場合、テキスト エディターは任意の言語に固有のコマンドせず、既定のショートカット メニューを提供します。 このメニューのコマンドは、コマンドを処理し、ショートカット メニューを表示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、ユーザーは、ctrl キーを押しながら J キーを入力したときに送信します。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ステートメント入力候補のボックスを表示します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが文字を入力したときに送信されます。 このコマンドをトリガーの文字が入力され、ステートメントの提供を補完、メソッドのヒント、および構文の色分け表示などのテキスト マーカーかっこの一致、およびエラーのマーカーを監視します。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>入力候補のおよび<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>メソッドに関するヒント</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>。 テキストのマーカーをサポートするには、文字の入力中に、マーカーを更新することが必要かどうかを判断するには、このコマンドを監視します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが Enter キーを入力したときに送信されます。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>メソッド</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>を呼び出してメソッド ヒントのウィンドウを無視するかを判断するには、このコマンドを監視します。 既定では、テキスト ビューは、このコマンドを処理します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーは、Backspace キーを入力したときに送信されます。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>メソッド</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>を呼び出してメソッド ヒントのウィンドウを無視するかを判断するようにモニター 既定では、テキスト ビューは、このコマンドを処理します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|メニューまたはショートカット キーから送信されます。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>パラメーター情報とヒントのウィンドウを更新する</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーは、変数にポインターを置くまたは変数にカーソルを配置し、選択時に送信**クイック ヒント**から**IntelliSense**で、**編集**メニュー。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>メソッド</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>を呼び出すことによって、ヒントで変数の型を返す デバッグが有効な場合は、ヒントは、変数の値も表示されます。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、ユーザーは、ctrl キーを押しながら space キーを入力したときに送信します。 このコマンドにより<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>メソッド</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>を呼び出す言語サービスに通知します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、メニューから送信された**選択範囲のコメント**または**選択範囲のコメントを解除**から**詳細設定**で、**編集**メニュー。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>ユーザーが選択したテキストをコメントにすることを示します<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>、ユーザーが選択されているテキストのコメントを解除することを示します</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>。</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> これらのコマンドは、言語サービスでのみ実装できます。|  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)
