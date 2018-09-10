---
title: 混合モード アプリケーションのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 795b1bf9f2c3d2014e1fa2c4ccd25254a07a70a8
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283315"
---
# <a name="debugging-mixed-mode-applications"></a>方法 : 混合モード アプリケーションをデバッグする
混合モード アプリケーションとは、ネイティブ コード (C++) とマネージド コード (共通言語ランタイムで動作する Visual Basic、Visual C#、C++ など) の組み合わせから成るアプリケーションです。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での混合モード アプリケーションのデバッグはきわめて透過的です。つまり、単一モードのアプリケーションをデバッグする場合とほとんど同じです。 ただし、特殊な注意事項があります。  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>混合モードのデバッグでの C++ のエディット コンティニュの有効化  

C++ のエディット コンティニュを有効にする、次を参照してください。[を有効にすると、エディット コンティニュを無効にする方法](../debugger/how-to-enable-and-disable-edit-and-continue.md)します。

> [!NOTE]
> Visual Studio 2013 で C++ に対してエディット コンティニュを使用するには、従来のデバッグ エンジンに戻る必要があります。 参照してください[Visual Studio 2013 でマネージ互換モードに切り替える](https://blogs.msdn.microsoft.com/devops/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013/)Microsoft アプリケーション ライフ サイクル管理ブログ。  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>混合モード アプリケーションでのプロパティ評価  
 混合モード アプリケーションでは、デバッガーを使用してプロパティを評価すると、負荷の高い操作になります。 そのため、ステップ実行などのデバッグ操作の処理速度が低下する場合があります。 詳細については、次を参照してください。[ステッピング](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100))します。 混合モードのデバッグでパフォーマンスが低下するような場合は、デバッガー ウィンドウのプロパティ評価をオフにできます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
#### <a name="to-turn-off-property-evaluation"></a>プロパティ評価をオフにするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **オプション**ダイアログ ボックスで、**デバッグ**フォルダーと選択、**全般**カテゴリ。  
  
3.  クリア、**プロパティの評価とその他の暗黙的な関数呼び出しを有効にする**チェック ボックスをオンします。  
  
 ネイティブな呼び出し履歴とマネージド呼び出し履歴は異なるため、デバッガーでは、混合コードに対して常に完全な呼び出し履歴を表示できるとは限りません。 ネイティブ コードがマネージド コードを呼び出したときに、不一致が生じていることがわかります。 詳細については、次を参照してください。[の混合コードと不足情報呼び出し履歴 ウィンドウで](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)します。  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)