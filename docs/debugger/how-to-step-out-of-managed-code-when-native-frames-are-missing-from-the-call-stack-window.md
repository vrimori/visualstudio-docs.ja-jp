---
title: ステップ アウトC#ネイティブ フレームが呼び出し履歴から不足しているときにコード |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2759df7cc59f4d0167e1ef44dfb9cc65d16ba815
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867437"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>方法: ネイティブ フレームが [呼び出し履歴] ウィンドウに見つからないときにマネージド コードからステップ アウトする

**[呼び出し履歴]** ウィンドウで表示されないネイティブ フレームがあるコードでは、マネージド コードからステップ アウトすると、予期しない結果になる場合があります。 代替手段として、**ステップ アウト**ではなくブレークポイントを使用できます。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[リセット設定](../ide/environment-settings.md#reset-settings)」を参照してください。

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>呼び出し履歴にネイティブ フレームが表示されないときにマネージド コードからステップ アウトする

1.  ネイティブ コード内で、マネージド コードの呼び出し後に位置ブレークポイントを設定します。

2.  **[デバッグ]** メニューの **[続行]** をクリックします。

     マネージド呼び出しが完了すると、ネイティブ コードのブレークポイントで実行が停止します。

## <a name="see-also"></a>関連項目

- [方法: [呼び出し履歴] ウィンドウを使用する](../debugger/how-to-use-the-call-stack-window.md)