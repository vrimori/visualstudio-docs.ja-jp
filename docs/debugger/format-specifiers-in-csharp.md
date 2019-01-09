---
title: 書式指定子でデバッガー (c#) |Microsoft Docs
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f01951a45a2e50f6dac093924627fe178011c9f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899015"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>C# では、Visual Studio デバッガーでの書式指定子
値を表示する形式を変更することができます、**ウォッチ**書式指定子を使用してウィンドウ。 書式指定子を使用することもできます、**イミディ エイト**ウィンドウで、**コマンド**ウィンドウで、[トレース ポイント](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)と、ソース ウィンドウ。 これらのウィンドウで式を一時停止する場合、結果に表示されます、[データヒント](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)指定した形式の表示にします。  
  
 書式指定子を使用するには、変数の式の後にコンマと、適切な指定子を入力します。  
  
## <a name="set-format-specifiers"></a>セットの書式指定子  
次のコード例を使用します。   
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 追加、`my_var1`変数を**ウォッチ**デバッグ中にウィンドウ**デバッグ** > **Windows** > **を見る** > **ウォッチ 1**します。 次に、変数を右クリックし  **16 進数表示**します。 これで、**ウォッチ**値 0x0065 がウィンドウに表示されます。 16 進数の整数ではなく、10 進整数としてこの値を確認するには、10 進書式指定子を追加 **、d**で、**名前**変数名の後の列。 **値**列が表示されます**101**します。   
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>書式指定子  
 次の表、 C# Visual Studio デバッガーの指定子の書式を設定します。  
  
|指定子|形式|元の [ウォッチ] の値|表示|  
|---------------|------------|--------------------------|--------------|  
|ac|プロパティと暗黙的関数呼び出しの暗黙の評価がになっている場合に利用でき、式の評価を強制します。|メッセージ "暗黙的な関数の評価はユーザーによってオフにされました"|\<value>|  
|d|10 進整数|0x0065|101|  
|dynamic|動的ビューを使用して、指定されたオブジェクトを表示します。|動的ビューを含む、オブジェクトのすべてのメンバーを表示します。|動的ビューのみが表示されます。|  
|h|16 進整数|61541|0x0000F065|  
|nq|引用符なしの文字列。|"My String"|My String|  
|nse|形式ではなく、動作を指定します。 「副作用なし」を使用して式を評価します。 式を解釈できません (関数呼び出し) などの評価でしか解決できない場合は、代わりにエラーが表示されます。|N/A|N/A|
|hidden|パブリック メンバーとパブリックでないメンバーをすべて表示します。|パブリック メンバーを表示します。|すべてのメンバーを表示します。|  
|raw|未処理の項目ノードで表示されるように項目を表示します。 プロキシ オブジェクトのみで有効です。|ディクショナリ\<T >|ディクショナリの未加工ビュー\<T >|  
|results|IEnumerable または IEnumerable を実装する型の変数と共に使用\<T >、通常はクエリ式の結果。 クエリ結果を含むメンバーのみを表示します。|すべてのメンバーを表示します|クエリの条件に一致するメンバーを表示します|  
  
## <a name="see-also"></a>関連項目  
 [ウォッチ ウィンドウと [クイック ウォッチ] ウィンドウ](../debugger/watch-and-quickwatch-windows.md)   
 [[自動変数] ウィンドウと [ローカル] ウィンドウ](../debugger/autos-and-locals-windows.md)
