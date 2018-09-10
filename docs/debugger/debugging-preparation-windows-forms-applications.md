---
title: 'デバッグの準備: Windows フォーム アプリケーション |Microsoft Docs'
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
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ec3fff82fcdc8db8328d1129a860495d081be2e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282813"
---
# <a name="debugging-preparation-windows-forms-applications"></a>デバッグの準備 : Windows フォーム アプリケーション
Windows フォーム プロジェクト テンプレートは、Windows フォーム アプリケーションを作成します。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、この種類のアプリケーションを簡単にデバッグできます。 詳細については、次を参照してください。 [Windows アプリケーション プロジェクトを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))します。  
  
 プロジェクト テンプレートを使用して Windows フォーム プロジェクトを作成する場合、デバッグ構成とリリース構成に必要な設定は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって自動的に作成されます。 この設定は必要に応じて変更できます。 これらの設定を変更することができます、 **\<プロジェクト名 > プロパティ ページ** ダイアログ ボックス (**My Project** Visual Basic で)。  
  
 詳細については、次を参照してください。[推奨プロパティ設定](../debugger/managed-debugging-recommended-property-settings.md)します。  
  
 推奨される追加のプロパティ設定を次の表に示します。  
  
### <a name="configuration-properties-in-debug-tab"></a>[デバッグ] タブの構成プロパティ  
  
|**プロパティ名**|**設定**|  
|-----------------------|-----------------|  
|**開始アクション**|-設定**スタート プロジェクト、** ほとんどの時間。 設定**外部プログラムの開始**を別の実行可能ファイルを開始する場合とデバッグを開始する (通常は Dll のデバッグ)。|  
  
 Windows フォーム アプリケーションは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内から、または既に実行中のアプリケーションにアタッチすることによってデバッグできます。 インポートに関する詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>C#、F#、または Visual Basic の Windows フォーム アプリケーションをデバッグするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクトを開きます。  
  
2.  必要に応じて、ブレークポイントを作成します。  
  
     Windows フォーム アプリケーションはイベント ドリブンであるため、ブレークポイントはイベント ハンドラー コード内またはイベント ハンドラー コードによって呼び出されるメソッド内に設定します。 ブレークポイントが配置される一般的なイベントは次のとおりです。  
  
    1.  Click、Enter などのコントロールに関連付けられたイベント。  
  
    2.  Load、Activated など、アプリケーションの起動またはシャットダウンに関連付けられたイベント。  
  
    3.  フォーカス イベントと検証イベント。  
  
     詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms)」を参照してください。  
  
3.  **デバッグ** メニューのをクリックして**開始**します。  
  
4.  説明した手法を使用してデバッグ[デバッガーの基本事項](../debugger/getting-started-with-the-debugger.md)します。  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [方法: セット デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [実行中のプロセスをアタッチします。](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows フォーム](/dotnet/framework/winforms/index)