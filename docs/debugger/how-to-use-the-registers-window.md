---
title: デバッガーでのレジスタ値を表示 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfc0482152b3da0b52950ab6389cc9f7d9e83e3a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974281"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>[レジスタ] ウィンドウで、レジスタの値を表示 (C#、C++、Visual Basic、 F#)

**登録**Visual Studio のデバッグ中に、レジスタの内容をウィンドウが表示されます。 レジスタの背後にある概念について大まかな概要について、**登録**ウィンドウを参照してください[デバッグの基礎: [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)します。

> [!NOTE]
> 登録情報は、スクリプトや SQL アプリのご利用いただけません。

デバッグ中に、アプリでコードの実行時の値の変更を登録します。 変更した値が赤で最近表示、**登録**ウィンドウ。

**[レジスタ]** ウィンドウでは、見やすいようにレジスタがグループ別に整理されますが、グループはプラットフォームやプロセッサの種類によって異なります。 表示したり、登録グループを非表示にすることができます。 詳細については、「[方法 :レジスタ グループの表示と非表示を切り替える](../debugger/how-to-display-and-hide-register-groups.md)」をご覧ください。

レジスタの値は編集できます。 詳細については、「[方法 :レジスタ値を編集する](../debugger/how-to-edit-a-register-value.md)」をご覧ください。

**[レジスタ] ウィンドウを開く**

1. 選択して、アドレス レベルのデバッグを有効にする**アドレス レベルのデバッグを有効にする**で**ツール**(または**デバッグ**) >**オプション** > **デバッグ**します。

1. デバッグが、実行中またはブレークポイントで、選択**デバッグ** > **Windows** > **登録**、またはキーを押します**Alt**+ **5**します。

>[!NOTE]
>ダイアログ ボックスとメニュー コマンドは、Visual Studio のエディションまたは設定によって異なる場合があります。 設定を変更するには、次のように選択します。**インポートおよびエクスポート設定**Visual Studio で**ツール**メニュー。 詳細については、「[リセット設定](../ide/environment-settings.md#reset-settings)」を参照してください。

### <a name="see-also"></a>関連項目

- [デバッグの基礎: [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)
- [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)
