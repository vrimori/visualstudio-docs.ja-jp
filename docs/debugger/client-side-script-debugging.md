---
title: クライアント側スクリプトのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a42ee63b863393c3cc2bad789d14404def8d1f5d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894990"
---
# <a name="client-side-script-debugging"></a>クライアント側スクリプトのデバッグ
Visual Studio デバッガーには、ASP.NET ページ内のクライアント側スクリプトのエラーを検出および修正するための包括的なデバッグ環境が用意されています。  
  
## <a name="opening-script-documents"></a>スクリプト ドキュメントを開く  
サーバー側およびクライアント側スクリプト ドキュメントの一覧を表示することができます、**ソリューション エクスプ ローラー**を表示します。 **ソリューション エクスプローラー**で、任意のスクリプト ドキュメントを開くことができます。 詳細については、「 [How to: View Script Documents](../debugger/how-to-view-script-documents.md)」を参照してください。  
  
## <a name="breakpoint-mapping"></a>ブレークポイントのマップ  
 Visual Studio では、サーバー側コードを直接デバッグすることはできませんが、サーバー側ファイルにブレークポイントを設定できます。 Visual Studio では、設定されたブレークポイントがクライアント側ファイルの対応する場所に自動的にマップされ、マップされたブレークポイントがクライアント側コードに作成されます。  
  
## <a name="manually-or-automatically-attaching-to-script"></a>手動または自動によるスクリプトへのアタッチ  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]でスクリプトをデバッグするには、デバッグするスクリプトにデバッガーをアタッチする必要があります。 これは手動で行うことも、自動的に行うこともできます。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガー インターフェイスを使用して、アタッチする実行中のスクリプト プロセスを選択することにより、手動でアタッチできます。 詳細については、「 [How to: Attach to Script](../debugger/how-to-attach-to-script.md)」を参照してください。  
  
 次のいずれかの状況が発生すると、デバッガーは自動的にスクリプトにアタッチされます。  
  
- スクリプトに設定されているブレークポイントにヒットした。  
  
- スクリプト コード内の VBScript `Stop` ステートメントまたは JScript `debugger` ステートメントにヒットした。  
  
- ブラウザーまたはサーバーが、スクリプト内で構文エラーまたはランタイム エラーを検出した。 これが発生すると、ダイアログ ボックスが表示され、デバッグを開始できます。  
  
  手動でスクリプトにアタッチした場合、そのスクリプト プロセスは、何らかの理由で停止するまで、引き続き実行されます。 **[デバッグ]** メニューの **[中断]** を選択することによって、プロセスを停止できます。  
  
  デバッガーが自動的にアタッチされると、スクリプトの実行は、ブレークポイント、 `Stop` ステートメント、 `debugger` ステートメント、またはエラーが発生した行、あるいは Internet Explorer でデバッグを開始するように選択した位置で停止します。  
  
  この時点で、通常のデバッガー機能を使用してデバッグを開始できます。 たとえば、 **[ステップ]** コマンドを使用すると、コードを行単位で継続して実行できます。 **[呼び出し履歴]** ウィンドウを使用して、スクリプトのフローの表示と制御を行うことができます。 変数ウィンドウまたは **イミディエイト** ウィンドウを使用して、変数およびプロパティの表示または変更を行うことができます。  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>スクリプト デバッグのための強化されたエラー メッセージ  
 Visual Studio では、一般的なスクリプトのデバッグ問題を示すエラー メッセージが強化されています。 これらのメッセージは、Internet Explorer に手動でアタッチした場合のみ表示されます。 Internet Explorer が自動的に開かれたときにエラー状態が検出される場合は、手動でアタッチするとエラー メッセージが表示されます。  
  
## <a name="debugging-ajax-script-applications"></a>AJAX スクリプト アプリケーションのデバッグ  
 AJAX 対応の Web アプリケーションではスクリプト コードを頻繁に使用するため、デバッグは困難になる可能性があります。 AJAX をデバッグする手法の詳細については、次を参照してください。  
  
 [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)で、任意のスクリプト ドキュメントを開くことができます。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET および AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [スクリプトのデバッグに関する制限事項](../debugger/limitations-on-script-debugging.md)   
 [変数 Windows](../debugger/debugger-windows.md)   
 [イミディエイト ウィンドウ](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
