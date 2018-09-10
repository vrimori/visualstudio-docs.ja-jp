---
title: '方法: 最適化されたコードのデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47b26883d0800611f2fba5cbf7a02907fef1d948
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280819"
---
# <a name="how-to-debug-optimized-code"></a>方法 : 最適化されたコードをデバッグする
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
> [!NOTE]
>  [(デバッグ機能の強化に最適化された)/Zo](/cpp/build/reference/zo-enhance-optimized-debugging)(Visual Studio Update 3 で導入) コンパイラ オプションには、最適化されたコードに関する豊富なデバッグ情報が生成されます (に組み込まれていないプロジェクト、 **/Od**コンパイラ オプション。 参照してください[/O オプション (コードの最適化)](/cpp/build/reference/o-options-optimize-code))。 これにはローカル変数とインライン関数のデバッグのサポートの強化が含まれます。  
>   
>  [エディット コンティニュ](../debugger/edit-and-continue-visual-csharp.md)場合は無効ですが、 **/Zo**コンパイラ オプションを使用します。  
  
 コンパイラは、ソース コードを最適化するときに命令を再配置したり再構成したりします。 これにより、コンパイル後のコードの実行効率が向上します。 しかし、この命令の整理が原因となり、一連の命令に対応するソース コードをデバッガーが識別できなくなる場合があります。  
  
 最適化によって次のような影響が生じる場合があります。  
  
-   ローカル変数がオプティマイザーによって削除されたり、デバッガーの追跡できない場所に移動されたりする可能性があります。  
  
-   オプティマイザーによってコード ブロックがマージされた場合、関数内の位置が変更されます。  
  
-   オプティマイザーによって 2 つの関数がマージされた場合、呼び出し履歴上のフレームに対し、間違った関数名が表示される場合があります。  
  
 ほとんどの場合、呼び出し履歴上のフレームには、正しい情報が表示されます。ただし、これはすべてのフレームにシンボルが割り当てられていることが前提です。 スタックの破損が生じた場合、アセンブリ言語で記述された関数が存在する場合、呼び出し履歴上のシンボルに一致しないオペレーティング システムのフレームが存在する場合など、呼び出し履歴上のフレームに誤った情報が表示されることがあります。  
  
 グローバル変数および静的変数は常に正しく表示されます。 構造体レイアウトについても同様です。 構造体へのポインターが存在し、そのポインターの値が正しければ、構造体のすべてのメンバー変数は、正しい値で表示されます。  
  
 これらの制限事項のため、できるだけ最適化する前のプログラムをデバッグするようにしてください。 既定では、最適化に対する設定は、Visual C++ プログラムのデバッグ構成ではオフ、リリース構成ではオンになっています。  
  
 ただし、最適化後のプログラムでしかバグが発生しない場合もあります。 このような場合は、最適化されたコードをデバッグする必要があります。  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>デバッグ ビルド構成で最適化をオンにするには  
  
1.  新しいプロジェクトの作成時に、`Win32 Debug` ターゲットを選択します。 使用して、`Win32``Debug`なるまで、プログラムを完全にデバッグおよびビルドする準備が整ったら、`Win32 Release`ターゲット。 コンパイラは、`Win32 Debug` ターゲットの最適化は行いません。  
  
2.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
3.  **ビュー**  メニューのをクリックして**プロパティ ページ**します。  
  
4.  **プロパティ ページ** ダイアログ ボックスに、必ず`Debug`でが選択されている、**構成**ドロップダウン リスト。  
  
5.  左側のフォルダー ビューで、選択、 **C/C++** フォルダー。  
  
6.  で、 **C++** フォルダーで、`Optimization`します。  
  
7.  右側のプロパティ リストで、[`Optimization`] を探します。 その横にある設定`Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`します。 その他のオプションのいずれかを選択 (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`、 `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`、 `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)`、または`Custom`)。  
  
8.  [`Custom`] に対して [`Optimization`] オプションを選択すると、プロパティ リストに表示されているその他のプロパティについてオプションを設定できるようになります。  
  
9. 構成プロパティ、C と C++ のプロジェクト プロパティ ページで、コマンド ライン ノードを選択し、追加`(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)`を**追加オプション**テキスト ボックス。  
  
    > [!WARNING]
    >  `/Zo` には、Visual Studio 2013 更新プログラム 3 以降のバージョンが必要です。  
    >   
    >  追加`/Zo`が無効になります[エディット コンティニュ](../debugger/edit-and-continue-visual-csharp.md)します。  
  
 最適化されたコードをデバッグするときに使用して、**逆アセンブル**命令が実際に作成され、実行を表示するウィンドウ。 ブレークポイントを設定する場合は、ブレークポイントが命令と共に移動する可能性があるため注意が必要です。 次に例を示します。  
  
```cpp
for (x=0; x<10; x++)  
```  
  
 この行にブレークポイントを設定したとします。 ブレークポイントは 10 回ヒットするように思われますが、このコードを最適化した場合、ブレークポイントは 1 回しかヒットしません。 これは、最初の命令によって `x` の値が 0 に設定されるためです。 コンパイラは、その最初の命令を 1 回だけ実行すると見なしてループの外に移動します。 このとき、ブレークポイントもこの命令と共に移動します。 `x` を比較してインクリメントする命令はループ内に残ったままになります。 表示すると、**逆アセンブリ**ウィンドウで、[ステップ単位](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100))より詳細に制御、最適化されたコードをステップ実行している場合に有用な命令に自動的に設定します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)
