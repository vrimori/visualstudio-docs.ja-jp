---
title: Windows サービスをデバッグするための準備 |Microsoft Docs
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
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86a80c6c24fdba594a5bfb5c11650b69eb2de693
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065013"
---
# <a name="debugging-preparation-windows-services"></a>デバッグの準備:Windows サービス
Windows サービスは、Microsoft Windows のバックグラウンドで実行されるプログラムです。 Windows サービスには、Telnet サービスや、コンピューターに表示される時計を更新する Windows タイム サービスなどがあります。 Windows サービスは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内から実行できないため、サービス コントロール マネージャーのコンテキストで実行する必要があります。 詳細については、「[Windows サービスの作成](/dotnet/framework/windows-services/how-to-create-windows-services)」、「[Windows サービス アプリケーションのデバッグ](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)」、および「[Windows サービス アプリケーション](/dotnet/framework/windows-services/index)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [方法: 方法 : OnStart メソッドをデバッグする](../debugger/how-to-debug-the-onstart-method.md)