---
title: "非同期 Windows ランタイム メソッドからの特別なエラー プロパティ | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>非同期 Windows ランタイム メソッドからの特別なエラー プロパティ
呼び出し履歴の深い場所からエラーがスローされる可能性があるため、JavaScript で非同期の Windows ランタイム メソッドをデバッグするのは困難な場合があります。 JavaScript の `Error` オブジェクトには追加のプロパティがあり、これらはアプリがデバッグ モードで実行されているときに非同期の Windows ランタイム メソッドからエラーがスローされた場合にのみ表示されます。  
  
## <a name="special-error-properties"></a>特別なエラー プロパティ  
 デバッグ モードで Windows ランタイムの非同期操作に失敗した結果として生じるエラー オブジェクトには、次の特別なプロパティがあります。  
  
-   `asyncOpSource` (オブジェクト) は、エラーの原因となった呼び出しが行われた元の場所に関する情報を取得します。 プロパティ `asyncOpSource.originatingCall` (文字列) は、非同期操作を開始した場所をユーザー コード内で表示します。  
  
-   asyncOpType (文字列) は、エラーの原因となった非同期操作の型の名前を取得します。  
  
 非同期操作でのエラーの詳細については、以下を参照してください。  
  
-   [promise を使ってエラーを処理する方法 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Windows ランタイム エラーのトラブルシューティング (HTML)](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)
