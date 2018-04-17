---
title: '方法: ネイティブ フレームが呼び出し履歴 ウィンドウから不足とマネージ コードからステップ アウト |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 5c64016f5ca0613a2986ec8a0bf305d88ecffd64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>方法 : ネイティブ フレームが [呼び出し履歴] ウィンドウに見つからないときにマネージ コードからステップ アウトする
かどうか、コードがネイティブ フレームでは表示されませんが、**呼び出し履歴**ウィンドウで、マネージ コード外のステップは、予期しない結果を生成できます。 この問題を回避するには、代わりにブレークポイントを使用することができます**ステップ アウト**です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>呼び出し履歴にネイティブ フレームが表示されないときにマネージ コードからステップ アウトするには  
  
1.  ネイティブ コード内で、マネージ コードの呼び出し後に位置ブレークポイントを設定します。  
  
2.  **デバッグ**] メニューの [選択**続行**です。  
  
     マネージ呼び出しが完了すると、ネイティブ コードのブレークポイントで実行が停止します。  
  
## <a name="see-also"></a>関連項目  
 [方法 : [呼び出し履歴] ウィンドウを使用する](../debugger/how-to-use-the-call-stack-window.md)