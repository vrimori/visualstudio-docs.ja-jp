---
title: "方法: エラー マーカーを実装して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d41c1bf063ea074df217934a00f73291a10e051d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-error-markers"></a>方法: エラー マーカーを実装します。
エラー マーカー (または赤色の波下線) は、テキスト エディターのカスタマイズを実装するが最も難しいです。 ただし、VSPackage のユーザーに提供する利点を提供するためのコストを上回ることができます。 エラー マーカーは微妙に、言語パーサーが波または波赤色の線で正しくないと判断されるテキストをマークします。 このインジケーターには、視覚的に不適切なコードを表示してプログラマが役立ちます。  
  
 テキスト マーカーを使用すると、赤色の波下線を実装します。 原則として、言語サービス追加赤色の波下線テキスト バッファーをバック グラウンド パスとしてアイドル時、またはバック グラウンド スレッドでします。  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>赤色の波下線付きの機能を実装するには  
  
1.  赤の波線を配置するテキストを選択します。  
  
2.  型のマーカーを作成する`MARKER_CODESENSE_ERROR`です。 詳細については、次を参照してください。[する方法: 標準のテキスト マーカーの追加](../extensibility/how-to-add-standard-text-markers.md)です。  
  
3.  その後、渡す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイス ポインター。  
  
 このプロセスでは、指定されたマーカーにツールヒントのテキストまたは特別なコンテキスト メニューを作成することもできます。 詳細については、次を参照してください。[する方法: 標準のテキスト マーカーの追加](../extensibility/how-to-add-standard-text-markers.md)です。  
  
 エラー マーカーを表示する前に、次のオブジェクトが必要です。  
  
-   パーサー。  
  
-   タスク プロバイダー (の実装は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) 再解析する行を識別するために行情報の変更の記録を保持します。  
  
-   ビューを使用して、カレットをキャプチャするテキストの表示フィルターの変更イベント、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) メソッドです。  
  
 パーサーでタスク プロバイダーとフィルターは、エラー マーカーを可能にするために必要なインフラストラクチャを提供します。 次の手順では、エラー マーカーを表示するため、プロセスを提供します。  
  
1.  フィルター選択されるビューでは、フィルターは、そのビューのデータに関連付けられているタスク プロバイダーへのポインターを取得します。  
  
    > [!NOTE]
    >  メソッドのヒント、ステートメント入力候補、エラー マーカーを同じコマンド フィルターを使用することができます。  
  
2.  フィルターを別の行に移動したことを示すイベントを受信すると、エラーをチェックするタスクが作成されます。  
  
3.  タスク ハンドラーは、行がダーティかどうかを確認します。 場合は、エラーの行を解析します。  
  
4.  エラーが見つかった場合、タスク プロバイダーは、作業項目インスタンスを作成します。 このインスタンスでは、環境が、テキスト ビューではエラー マーカーとして使用するテキスト マーカーを作成します。  
  
## <a name="see-also"></a>参照  
 [レガシ API でテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキストのマーカーの追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: テキスト マーカーを使用](../extensibility/how-to-use-text-markers.md)