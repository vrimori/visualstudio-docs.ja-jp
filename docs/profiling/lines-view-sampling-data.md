---
title: "行ビュー - サンプリング データ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31cd3b1732cb279004eb500b5df6583a04d2e7bb
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="lines-view---sampling-data"></a>行ビュー - サンプリング データ
サンプリング データの [行] ビューには、プロファイリングを実行してサンプルを収集するときに実行したステートメントのパフォーマンス データが表示されます。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 UWP アプリにも新しい収集手法が必要です。 ｢[Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール)」をご覧ください。  
  
 ソース ファイルでは、1 つのステートメントを複数の行にわたって記述することも、複数のステートメントを 1 つの行に含めることもできます。 ステートメントは、次の項目によって識別されます。  
  
-   function ステートメントを含むソース ファイル。  
  
-   ステートメントを含む関数。  
  
-   ステートメントが開始されるソース行。  
  
-   ステートメントが開始されるソース行の文字。  
  
-   ステートメントが終了するソース行。  
  
-   ステートメントが終了するソース行の文字。  
  
 [ソース/行番号] 列は、識別子データを連結したもので、この列による並べ替えが可能です。  
  
 定義上、ステートメントは他の関数を呼び出しません。 そのため、排他的な値のみが一覧表示されます。  
  
|Column|説明|  
|------------|-----------------|  
|**プロセス ID**|プロファイリング実行のプロセス ID (PID) です。|  
|**プロセス名**|プロセスの名前です。|  
|**モジュール名**|関数行を含むモジュールの名前です。|  
|**モジュール パス**|関数行を含むモジュールのパスです。|  
|**ソース ファイル**|関数行を含むソース ファイルです。|  
|**関数名**|関数の名前。|  
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|  
|**関数アドレス**|関数の開始アドレスです。|  
|**ソース開始行**|このサンプルが収集されたソース ファイル内の開始行番号です。|  
|**ソース終了行**|このサンプルが収集されたソース ファイル内の終了行番号です。|  
|**ソース開始文字番号**|このサンプルが収集されたソース ファイル行内の開始文字のオフセットです。|  
|**ソース終了文字番号**|このサンプルが収集されたソース ファイル行内の終了文字のオフセットです。|  
|**ソース/行番号**|`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number End`**,**`Character End`**]** という構文を持つ、プロファイラーによって生成された行の識別子です。|  
|**サンプル数 (関数のみ)**|関数行を実行していたときに収集されたサンプルの合計数です。|  
|**サンプル % (関数のみ)**|関数行を実行していたときに収集された、プロファイリング実行内のすべてのサンプルの割合です。|  
  
## <a name="see-also"></a>関連項目  
 [行ビュー - サンプリング](../profiling/lines-view-dotnet-memory-sampling-data.md)