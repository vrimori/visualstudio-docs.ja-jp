---
title: In the Debugger in Visual Studio の逆アセンブリ コードの表示 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/30/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9cf75915b3ca17df1ee9e2ef41040147c146ea8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52387670"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio デバッガーでの逆アセンブリ コードの表示 (C#、C++、Visual Basic、 F#)

**[逆アセンブル]** ウィンドウには、コンパイラによって作成された命令に対応するアセンブリ コードが表示されます。 マネージ コードをデバッグしている場合、これらのアセンブリ命令はない Microsoft intermediate language (MSIL) Visual Studio コンパイラによって作成された、ジャストイン タイム (JIT) コンパイラによって作成されたネイティブ コードに対応します。

> [!NOTE]
> フル活用するために、**逆アセンブル**ウィンドウで、理解したりの基礎を習得[アセンブリ言語プログラミング](https://wikipedia.org/wiki/Assembly_language)します。

この機能を使用できるは、アドレス レベルのデバッグが有効になっている場合だけです。 スクリプトまたは SQL デバッグは使用できません。

**[逆アセンブル]** ウィンドウでは、アセンブリ命令だけでなく、必要に応じて以下の情報も表示できます。

- 各命令が配置されているメモリ アドレス。 ネイティブ アプリケーションの場合は、実際のメモリ アドレス。 Visual basic またはC#は、関数の先頭からのオフセット。

- アセンブリ コードの派生元のソース コード。

- コード バイト、つまり、実際のコンピューターまたは MSIL 命令のバイト。

- メモリ アドレスのシンボル名。

- ソース コードに対応する行番号。

アセンブリ言語命令から成る*ニーモニック*、命令名の省略形であると*シンボル*変数、レジスタ、および定数。 各マシン語命令は、必要に応じて、1 つまたは複数のシンボルを続けて 1 つのアセンブリ言語ニーモニックで表現されます。

アセンブリ コードは、プロセッサのレジスタに大きく依存または、マネージ コードは、共通言語ランタイムを登録します。 使用することができます、**逆アセンブル**ウィンドウと共に、**登録**ウィンドウで、レジスタの内容を調べることができます。

アセンブリ言語ではなく、未加工の数値形式では、マシン語コード命令を表示するには、使用、**メモリ**ウィンドウまたは選択**コード バイト**のショートカット メニューから、**逆アセンブリ**ウィンドウ。

## <a name="use-the-disassembly-window"></a>逆アセンブル ウィンドウを使用します。

有効にする、**逆アセンブル**ウィンドウで、**ツール** > **オプション**(または**ツール** >  **オプション**) >**デバッグ**、**アドレス レベルのデバッグを有効にする**します。

開くには、**逆アセンブル**デバッグ中に、ウィンドウ**Windows** > **逆アセンブル**またはキーを押します**Alt** + **8**します。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、次を参照してください。[設定にリセット](../ide/environment-settings.md#reset-settings)します。

右クリック オプションの情報をオンまたはオフ、**逆アセンブリ**ウィンドウで、設定や、ショートカット メニューで目的のオプションをオフにします。

左余白の黄色の矢印は、現在の実行ポイントをマークします。 ネイティブ コードの実行ポイントは、CPU のプログラム カウンターに対応します。 この位置は、プログラム内で次に実行される命令を示します。

## <a name="see-also"></a>関連項目

* [ページ単位の上下移動 (メモリ内での)](../debugger/how-to-page-up-or-down-in-memory.md)
* [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)
* [方法: [レジスタ] ウィンドウを使用する](../debugger/how-to-use-the-registers-window.md)