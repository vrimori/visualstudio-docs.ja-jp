---
title: 混合モード デバッグ プロセスが Microsoft.NET Framework 4 を使用する場合にのみサポートされている x64 より |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6d58713da9a4c809d5f9c3db6f7157a699a467f
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284095"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>x64 プロセスの混合モード デバッグは、4 より前の Microsoft .NET Framework バージョンを使用している場合にはサポートされません。
バージョンが 4 より前の .NET Framework では、x64 プロセスの混合モード デバッグはサポートされません。 つまり、デバッグ中にマネージド コードからネイティブ コードにステップ インすることや、ネイティブ コードからマネージド コードにステップ インすることはできません。  
  
### <a name="workarounds"></a>問題回避  
  
-   Microsoft .NET Framework 4 以降を使用するようにプロジェクトを更新する。  
  
     - または -  
  
     マネージド コードとネイティブ コードを個別のデバッガー セッション内でデバッグする。  
  
     - または -  
  
     次の手順に示すように、混合コードを 32 ビット プロセスとしてデバッグする。  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>プラットフォームを 32 ビットに変更するには (Visual Basic または C#)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**します。  
  
2.  [プロパティ ページ] でをクリックして、**コンパイル**または**デバッグ**タブ。  
  
3.  クリックして**プラットフォーム**プラットフォームの一覧から x86 を選択します。  
  
     Visual Basic コンパイラおよび C# コンパイラの既定では、どの CPU 上でも実行されるコードが生成されます。 64 ビット コンピューター上では、これらのバイナリは 64 ビット プロセスとして実行されます。 選択する必要があります、32 ビット プロセスで実行する**Win32**ではなく、 **AnyCPU**します。  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>プラットフォームを 32 ビットに変更するには (C/C++)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**します。  
  
2.  [プロパティ ページ] でクリックして**プラットフォーム**Win32 をプラットフォームの一覧から選択します。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   参照してください[SQL デバッグ セットアップ](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))します。  
  
## <a name="see-also"></a>関連項目  
 [64 ビット アプリケーションをデバッグする](../debugger/debug-64-bit-applications.md)