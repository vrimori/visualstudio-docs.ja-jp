---
title: 'マネージ デバッグ: プロパティの設定をお勧めします |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c82a624e5a2847da5c0f85a9e2ef4180a338a34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724695"
---
# <a name="managed-debugging-recommended-property-settings"></a>マネージド デバッグ : プロパティの推奨設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

一部のプロパティは、すべてのマネージド デバッグ シナリオで同じように設定する必要があります。  
  
 プロパティの推奨設定を以下に示します。  
  
 ここに記載されていない設定は、マネージド プロジェクトの種類によって異なる場合があります。 たとえば、**開始動作**よりも Windows フォーム プロジェクトで設定が異なりますが、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]プロジェクト。  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>[ビルド] タブ (C#) または [コンパイル] タブ (Visual Basic) の構成プロパティ  
  
|**プロパティ名**|**設定**|  
|-----------------------|-----------------|  
|**定数 DEBUG の定義**|C# および F#: チェック ボックスをオンに設定します。 これにより、アプリケーションで Debug クラスを使用できます。|  
|**定数 TRACE の定義**|C# および F#: チェック ボックスをオンに設定します。 これにより、アプリケーションで Trace クラスを使用できます。|  
|**コードの最適化**|C#、F#、および Visual Basic: false に設定します。 最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。 プログラムが最適化されたコードにだけ現れるバグを発見した場合は、この設定を有効しますが、コードに示すように、**逆アセンブル**ウィンドウが、コードに表示される内容が一致しないがあります最適化されたソースから生成されました。エディターです。 最適化されたコードをデバッグするには、オフにする必要があります[マイ コードのみ](just-my-code.md)します。<br /><br /> 詳細については、次を参照してください。 [c# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)または[Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)します。|  
|**出力パス**|Bin \debug に設定\\します。|  
|**詳細コンパイル オプション**|Visual Basic のみ。 クリックして**詳細**次の表に記載されている高度なプロパティを設定します。|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>[ビルドの詳細設定] ダイアログ ボックス  
  
|**プロパティ名**|**設定**|  
|-----------------------|-----------------|  
|**最適化を有効にする**|指定された理由で false に設定、**コードを最適化する**前の表のオプション。|  
|**デバッグ情報を生成します。**|このチェック ボックスをオンにすると、コンパイル時に /DEBUG フラグが設定され、デバッグを円滑に実行するうえで必要な情報が生成されます。|  
|**定数 DEBUG の定義**|このチェック ボックスをオンにすると、`DEBUG` 定数が定義され、アプリケーションで <xref:System.Diagnostics.Debug> クラスを使用できるようになります。|  
|**定数 TRACE の定義**|このチェック ボックスをオンにすると、`TRACE` 定数が定義され、アプリケーションで <xref:System.Diagnostics.Trace> クラスを使用できるようになります。|  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [C#、F#、および Visual Basic のプロジェクト](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)



