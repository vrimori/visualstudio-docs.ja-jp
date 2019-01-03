---
title: 言語の重要なコマンド サービス フィルター |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: e9f4c568722700ab4521f8a34a0639e78b9f550b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891697"
---
# <a name="important-commands-for-language-service-filters"></a>言語サービス フィルターの重要なコマンド
フル機能の言語サービス フィルターを作成する場合は、次のコマンドの処理を検討してください。 コマンド識別子の完全な一覧が定義されている、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>マネージ コードと Stdidcmd.h ヘッダーの列挙体のアンマネージ ファイル[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]コード。 Stdidcmd.h ファイル*Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc します。  
  
## <a name="commands-to-handle"></a>ハンドルするためのコマンド  
  
> [!NOTE]
>  場合によっては、次の表のすべてのコマンドのフィルター処理する必要はありません。  
  
|コマンド|説明|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーを右クリックしたときに送信されます。 このコマンドでは、ショートカット メニューを提供する時間があることを示します。 このコマンドを処理しない場合、テキスト エディターはなく、言語固有のコマンドの既定のショートカット メニューを提供します。 このメニューで、独自のコマンドは、コマンドを処理し、手動でショートカット メニューを表示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、ユーザーが CTRL + J を入力したときを送信します。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ステートメント入力候補のボックスを表示します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが文字を入力したときに送信されます。 トリガーの文字を入力し、ステートメントを指定する入力候補、メソッドのヒント、および構文の色分けなどのテキスト マーカーかっこの一致、時期を決定するには、このコマンドとエラーのマーカーを監視します。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ステートメント入力候補に対して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>メソッドのヒント。 テキスト マーカーをサポートするには、型指定されている文字が、マーカーを更新することが必要かどうかを判断するには、このコマンドを監視します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが Enter キーを入力したときに送信されます。 次のコマンドを呼び出すことによって、メソッドのヒント ウィンドウを無視する場合の判別を監視、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>します。 既定では、テキスト ビューは、このコマンドを処理します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーは、Backspace キーを入力したときに送信されます。 呼び出すことによってメソッドのヒント ウィンドウを閉じるタイミングを決定するモニター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>します。 既定では、テキスト ビューは、このコマンドを処理します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|メニューまたはショートカット キーから送信されます。 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>とパラメーター情報、ヒント ウィンドウを更新します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|ユーザーが変数上に置いたまたは変数にカーソルを位置付けます選択して、送信**クイック ヒント**から**IntelliSense**で、**編集**メニュー。 呼び出すことによって、ヒントで変数の型を返す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。 デバッグがアクティブな場合は、ヒント、変数の値を表示するもする必要があります。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、ユーザーが ctrl キーを押しながら space キーを入力したときに送信します。 このコマンドを呼び出す言語サービスに指示、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常、メニューから送信**選択範囲のコメント**または**選択範囲のコメントを解除します**から**詳細**で、**編集**メニュー。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ユーザーが選択したテキストをコメントにすることを示します<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>ユーザーが選択されているテキストのコメントを解除することを示します。 これらのコマンドは、言語サービスでのみ実装できます。|  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)