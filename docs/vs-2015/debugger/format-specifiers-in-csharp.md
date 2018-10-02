---
title: 書式指定子 (C#) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27c3dcf59068ca511f52850e328ef186c22b3dfa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546124"
---
# <a name="format-specifiers-in-c"></a>C# の書式指定子 #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[c# の書式指定子](https://docs.microsoft.com/visualstudio/debugger/format-specifiers-in-csharp)します。  
  
書式指定子を使用して、 **ウォッチ** ウィンドウに表示される値の書式設定を変更することができます。 また、 **[イミディエイト]** ウィンドウ、 **[コマンド]** ウィンドウ、およびソースのウィンドウでも、書式指定子を使用できます。 これらのウィンドウで式の上にカーソルを合わせると、結果が [データヒント] に表示されます。 [データヒント] には、[データヒント] 表示の書式指定子が反映されます。  
  
 書式指定子を使用するには、式に続いてコンマを入力します。 コンマの後に、適切な指定子を追加します。  
  
## <a name="using-format-specifiers"></a>書式指定子の使用  
 次のようなコードがあるとします。  
  
```  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 `my_var1` 変数をウォッチ ウィンドウに追加し (デバッグ中に **[デバッグ]/[ウィンドウ]/[ウォッチ]/、[ウォッチ 1]**)、表示を 16 進数に設定します ( **ウォッチ** ウィンドウで変数を右クリックし、 **[16 進数で表示]** を選択)。 これで、 **ウォッチ** ウィンドウに値 "0x0065" が表示されます。 この値を 16 進数の整数ではなく 10 進数の整数で表示するには、[名前] 列で変数名の後に 10 進数の書式指定子 **, d**を追加します。 [値] 列には、10 進数の値 "101" が表示されるようになりました。  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>書式指定子  
 デバッガーで認識される C# の書式指定子を次の表に示します。  
  
|指定子|形式|元の [ウォッチ] の値|表示|  
|---------------|------------|--------------------------|--------------|  
|ac|式を強制的に評価します。 これは、プロパティの暗黙の評価および暗黙の関数呼び出しがオフの場合に便利です。 参照してください[Side Effects and Expressions](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)します。|メッセージ "暗黙的な関数の評価はユーザーによってオフにされました"|\<value>|  
|d|10 進整数|0x0065|101|  
|dynamic|動的ビューを使用して、指定されたオブジェクトを表示します。|動的ビューを含む、オブジェクトのすべてのメンバーを表示します。|動的ビューのみが表示されます。|  
|h|16 進整数|61541|0x0000F065|  
|nq|引用符なしの文字列。|"My String"|My String|  
|hidden|パブリック メンバーとパブリックでないメンバーをすべて表示します。|パブリック メンバーを表示します。|すべてのメンバーを表示します。|  
|raw|未処理の項目ノードで表示されるように項目を表示します。 プロキシ オブジェクトのみで有効です。|ディクショナリ\<T >|ディクショナリの未加工ビュー\<T >|  
|results|IEnumerable または IEnumerable を実装する型の変数と共に使用\<T >、通常はクエリ式の結果。 クエリ結果を含むメンバーのみを表示します。|すべてのメンバーを表示します。|クエリの条件に一致するメンバーを表示します。|  
  
## <a name="see-also"></a>関連項目  
 [ウォッチ ウィンドウと [クイック ウォッチ] の Windows](../debugger/watch-and-quickwatch-windows.md)   
 [変数 Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





