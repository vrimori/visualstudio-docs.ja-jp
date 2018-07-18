---
title: '方法: 最適化されたコードのデバッグ |Microsoft ドキュメント'
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
ms.openlocfilehash: 9610f71a197c47521e2139d40aff1afde6a8a894
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478081"
---
# <a name="how-to-debug-optimized-code"></a>方法 : 最適化されたコードをデバッグする
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
> [!NOTE]
>  [(強化に最適化されたデータのデバッグ)/Zo](/cpp/build/reference/zo-enhance-optimized-debugging)(Visual Studio Update 3 で導入) コンパイラ オプションには、最適化されたコードについて豊富なデバッグ情報が生成されます (プロジェクトに組み込まれていない、 **/Od**コンパイラ オプション。 参照してください[/O オプション (コードの最適化)](/cpp/build/reference/o-options-optimize-code))。 これにはローカル変数とインライン関数のデバッグのサポートの強化が含まれます。  
>   
>  [エディット コンティニュ](../debugger/edit-and-continue-visual-csharp.md)は無効になっている場合、 **/Zo**コンパイラ オプションを使用します。  
  
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
  
1.  新しいプロジェクトの作成時に、`Win32 Debug` ターゲットを選択します。 使用して、`Win32``Debug`対象とするまで、プログラムを完全にデバッグおよびビルドする準備ができたら、`Win32 Release`ターゲットです。 コンパイラは、`Win32 Debug` ターゲットの最適化は行いません。  
  
2.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
3.  **ビュー**  メニューのをクリックして**プロパティ ページ**です。  
  
4.  **プロパティ ページ** ダイアログ ボックスで確認`Debug`でが選択されている、**構成**ドロップダウン リスト。  
  
5.  左側のフォルダー ビューで、選択、 **C/C++** フォルダーです。  
  
6.  下にある、 **C++** フォルダーを選択`Optimization`です。  
  
7.  右側のプロパティ リストで、[`Optimization`] を探します。 その横の設定がになっているはず`Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`です。 その他のオプションのいずれかを選択 (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`、 `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`、 `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)`、または`Custom`)。  
  
8.  [`Custom`] に対して [`Optimization`] オプションを選択すると、プロパティ リストに表示されているその他のプロパティについてオプションを設定できるようになります。  
  
9. 構成プロパティ、C と C++ プロジェクト プロパティ ページのコマンドライン ノードを選択し、追加`(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)`を**追加オプション**テキスト ボックス。  
  
    > [!WARNING]
    >  `/Zo` には、Visual Studio 2013 更新プログラム 3 以降のバージョンが必要です。  
    >   
    >  追加`/Zo`が無効になります[エディット コンティニュ](../debugger/edit-and-continue-visual-csharp.md)です。  
  
 最適化されたコードをデバッグするときに使用して、**逆アセンブル**をどのような手順を実際に作成、実行を表示するウィンドウです。 ブレークポイントを設定する場合は、ブレークポイントが命令と共に移動する可能性があるため注意が必要です。 次に例を示します。  
  
```  
for (x=0; x<10; x++)  
```  
  
 この行にブレークポイントを設定したとします。 ブレークポイントは 10 回ヒットするように思われますが、このコードを最適化した場合、ブレークポイントは 1 回しかヒットしません。 これは、最初の命令によって `x` の値が 0 に設定されるためです。 コンパイラは、その最初の命令を 1 回だけ実行すると見なしてループの外に移動します。 このとき、ブレークポイントもこの命令と共に移動します。 `x` を比較してインクリメントする命令はループ内に残ったままになります。 表示すると、**逆アセンブル** ウィンドウで、[ステップ単位](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9)大きいコントロールは、最適化されたコードをステップ実行する場合に有用な命令に自動的に設定します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)