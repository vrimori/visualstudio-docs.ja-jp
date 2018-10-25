---
title: '方法: エラーのマーカーの実装 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb6e511fa899680338831f3bc8e2a411f2126006
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861164"
---
# <a name="how-to-implement-error-markers"></a>方法: エラーのマーカーの実装
エラーのマーカー (または赤色の波下線) は、テキスト エディターのカスタマイズを実装するが最も難しいです。 ただし、VSPackage のユーザーに提供する利点は、提供するコストを上回るまでことができます。 エラーのマーカーは、微妙、言語のパーサーが波線または波状の赤い線で正しくないと判断されるテキストをマークします。 このインジケーターには、不適切なコードを視覚的に表示することでプログラマが役立ちます。  
  
 テキスト マーカーを使用すると、赤い波線を実装します。 原則として、言語サービスに赤い波線がバッファーに追加テキスト、バック グラウンド パスとして、アイドル時、またはバック グラウンド スレッドでします。  
  
## <a name="to-implement-the-red-wavy-underline-feature"></a>赤い波線の機能を実装するには  
  
1. 赤い波線を配置するテキストを選択します。  
  
2. 型のマーカーを作成`MARKER_CODESENSE_ERROR`です。 詳細については、次を参照してください。[方法: 標準のテキスト マーカーを追加](../extensibility/how-to-add-standard-text-markers.md)します。  
  
3. その後、渡す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイス ポインター。  
  
   このプロセスでは、特定のマーカーにツールヒントのテキストまたは特別なコンテキスト メニューを作成することもできます。 詳細については、次を参照してください。[方法: 標準のテキスト マーカーを追加](../extensibility/how-to-add-standard-text-markers.md)します。  
  
   エラーのマーカーを表示する前に、次のオブジェクトが必要です。  
  
- パーサーです。  
  
- タスク プロバイダー (の実装は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) 再解析する行を識別するために行情報の変更の記録を保持します。  
  
- カレットをキャプチャするテキスト ビューのフィルターを使用して、ビューからイベントを変更する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) メソッドです。  
  
  パーサー、タスク プロバイダー、およびフィルターは、エラー マーカーを可能にするために必要なインフラストラクチャを提供します。 次の手順では、エラー マーカーを表示するため、プロセスを提供します。  
  
1.  フィルター選択されるビューでは、フィルターは、そのビューのデータに関連付けられているタスク プロバイダーへのポインターを取得します。  
  
    > [!NOTE]
    >  メソッドのヒント、ステートメント入力候補、エラーのマーカーを同じコマンド フィルターを使用することができます。  
  
2.  フィルターは、別の行に移動したことを示すイベントを受信、エラーをチェックするタスクが作成されます。  
  
3.  タスク ハンドラーでは、行のダーティを確認します。 そうである場合は、エラーの行を解析します。  
  
4.  エラーが見つかった場合、タスク プロバイダーは、作業項目のインスタンスを作成します。 このインスタンスは、テキスト ビューでエラーのマーカーとして、環境を使用してテキスト マーカーを作成します。  
  
## <a name="see-also"></a>関連項目  
 [テキスト マーカーを使用して、従来の API を使用しました。](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキスト マーカーの追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: カスタム テキスト マーカーの作成](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: テキスト マーカーを使用](../extensibility/how-to-use-text-markers.md)
