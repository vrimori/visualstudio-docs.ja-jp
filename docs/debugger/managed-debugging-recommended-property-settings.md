---
title: デバッガーのプロパティの設定をお勧めしますC#、VB |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 69b98fe00301ad9230cb4f560a0a1d9dc1d3922f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064959"
---
# <a name="managed-debugging-recommended-property-settings"></a>マネージド デバッグ:プロパティの推奨設定
一部のプロパティは、すべてのマネージド デバッグ シナリオで同じように設定する必要があります。  
  
 プロパティの推奨設定を以下に示します。  
  
 ここに記載されていない設定は、マネージド プロジェクトの種類によって異なる場合があります。 たとえば、**[開始動作]** は、Windows フォーム プロジェクトと [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロジェクトとで設定が異なります。  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>[ビルド] タブ (C#) または [コンパイル] タブ (Visual Basic) の構成プロパティ  
  
|**プロパティ名**|**設定**|  
|-----------------------|-----------------|  
|**定数 DEBUG の定義**|C#F#:チェック ボックスをオンに設定します。 これにより、アプリケーションで Debug クラスを使用できます。|  
|**定数 TRACE の定義**|C#F#:チェック ボックスをオンに設定します。 これにより、アプリケーションで Trace クラスを使用できます。|  
|**コードの最適化**|C#、 F#、および Visual Basic:False に設定します。 最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。 プログラムで、最適化されたコードだけに現れるバグが見つかった場合は、この設定を有効にできます。**[逆アセンブル]** ウィンドウに表示されるコードは最適化されたソースから生成されているため、コード エディターに表示されるコードとは一致しない可能性があります。 最適化されたコードをデバッグするには、[マイ コードのみ] をオフにする必要があります。 (「[ステップ実行をマイ コードのみに制限する](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)」を参照)。<br /><br /> 詳細については、次を参照してください。 [c# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)または[Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)します。|  
|**出力パス**|bin\Debug\\ に設定します。|  
|**詳細コンパイル オプション**|Visual Basic のみ。 **[詳細]** をクリックして、次の表に示す詳細なプロパティを設定できるようにします。|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>[ビルドの詳細設定] ダイアログ ボックス  
  
|**プロパティ名**|**設定**|  
|-----------------------|-----------------|  
|**最適化を有効にする**|指定された理由で false に設定、**コードを最適化する**前の表のオプション。|  
|**デバッグ情報の生成**|このチェック ボックスをオンにすると、コンパイル時に /DEBUG フラグが設定され、デバッグを円滑に実行するうえで必要な情報が生成されます。|  
|**定数 DEBUG の定義**|このチェック ボックスをオンにすると、`DEBUG` 定数が定義され、アプリケーションで <xref:System.Diagnostics.Debug> クラスを使用できるようになります。|  
|**定数 TRACE の定義**|このチェック ボックスをオンにすると、`TRACE` 定数が定義され、アプリケーションで <xref:System.Diagnostics.Trace> クラスを使用できるようになります。|  
  
## <a name="see-also"></a>参照  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [C#、F#、および Visual Basic のプロジェクト](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)