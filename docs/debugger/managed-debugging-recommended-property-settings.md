---
title: 'マネージ デバッグ: プロパティの推奨設定 |Microsoft ドキュメント'
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
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e51a57f1929f4ba63bb4117e6dc496b52f2c20a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="managed-debugging-recommended-property-settings"></a>マネージ デバッグ : プロパティの推奨設定
一部のプロパティは、すべてのマネージ デバッグ シナリオで同じように設定する必要があります。  
  
 プロパティの推奨設定を以下に示します。  
  
 ここに記載されていない設定は、マネージ プロジェクトの種類によって異なる場合があります。 たとえば、**開始動作**よりも、Windows フォーム プロジェクトで設定が異なりますが、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]プロジェクト。  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>[ビルド] タブ (C#) または [コンパイル] タブ (Visual Basic) の構成プロパティ  
  
|**プロパティ名**|**設定**|  
|-----------------------|-----------------|  
|**定数 DEBUG の定義**|C# および F#: チェック ボックスをオンに設定します。 これにより、アプリケーションで Debug クラスを使用できます。|  
|**定数 TRACE の定義**|C# および F#: チェック ボックスをオンに設定します。 これにより、アプリケーションで Trace クラスを使用できます。|  
|**コードの最適化**|C#、F#、および Visual Basic: false に設定します。 最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。 プログラムには、最適化されたコードにだけ現れるバグが見つかったら場合、することができます、この設定を有効にはそのコードに示すように、**逆アセンブル**ウィンドウは、コードで表示される内容が一致しないがあります最適化されたソースから生成エディターです。 最適化されたコードをデバッグするには、[マイ コードのみ] をオフにする必要があります。 (を参照してください[ステップ実行をマイ コードのみに制限する](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code))。<br /><br /> 詳細については、次を参照してください。 [c# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)または[Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)です。|  
|**出力パス**|Bin \debug に設定\\です。|  
|**詳細コンパイル オプション**|Visual Basic のみ。 をクリックして**詳細**次の表に記載されている高度なプロパティを設定します。|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>[ビルドの詳細設定] ダイアログ ボックス  
  
|**プロパティ名**|**設定**|  
|-----------------------|-----------------|  
|**最適化を有効にする**|指定された理由を false に設定、**コードを最適化する**上の表でオプションです。|  
|**デバッグ情報を生成します。**|このチェック ボックスをオンにすると、コンパイル時に /DEBUG フラグが設定され、デバッグを円滑に実行するうえで必要な情報が生成されます。|  
|**定数 DEBUG の定義**|このチェック ボックスをオンにすると、`DEBUG` 定数が定義され、アプリケーションで <xref:System.Diagnostics.Debug> クラスを使用できるようになります。|  
|**定数 TRACE の定義**|このチェック ボックスをオンにすると、`TRACE` 定数が定義され、アプリケーションで <xref:System.Diagnostics.Trace> クラスを使用できるようになります。|  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)   
 [C#、F#、および Visual Basic のプロジェクト](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)