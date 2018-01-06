---
title: "混合モード デバッグ プロセスは、microsoft.net Framework 4 を使用する場合にのみサポート x64 以上 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 37d5c52192c30ccc3b34bfa609c3f6a7ffb99566
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>x64 プロセスの混合モード デバッグは、4 より前の Microsoft .NET Framework バージョンを使用している場合にはサポートされません。
バージョンが 4 より前の .NET Framework では、x64 プロセスの混合モード デバッグはサポートされません。 つまり、デバッグ中にマネージ コードからネイティブ コードにステップ インすることや、ネイティブ コードからマネージ コードにステップ インすることはできません。  
  
### <a name="workarounds"></a>問題回避  
  
-   Microsoft .NET Framework 4 以降を使用するようにプロジェクトを更新する。  
  
     - または -  
  
     マネージ コードとネイティブ コードを個別のデバッガー セッション内でデバッグする。  
  
     - または -  
  
     次の手順に示すように、混合コードを 32 ビット プロセスとしてデバッグする。  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>プラットフォームを 32 ビットに変更するには (Visual Basic または C#)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**です。  
  
2.  プロパティ ページで、をクリックして、**コンパイル**または**デバッグ**タブです。  
  
3.  をクリックして**プラットフォーム**とプラットフォームの一覧から [x86] を選択します。  
  
     Visual Basic コンパイラおよび C# コンパイラの既定では、どの CPU 上でも実行されるコードが生成されます。 64 ビット コンピューター上では、これらのバイナリは 64 ビット プロセスとして実行されます。 で、32 ビット プロセスを実行する必要がありますを選択する**Win32**ではなく、 **AnyCPU**です。  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>プラットフォームを 32 ビットに変更するには (C/C++)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、**プロパティ**です。  
  
2.  プロパティ ページで、をクリックして**プラットフォーム**とプラットフォームの一覧から [Win32] を選択します。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   参照してください[SQL デバッグ セットアップ](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)です。  
  
## <a name="see-also"></a>参照  
 [64 ビット アプリケーションをデバッグする](../debugger/debug-64-bit-applications.md)