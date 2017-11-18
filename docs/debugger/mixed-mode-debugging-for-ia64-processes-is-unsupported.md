---
title: "IA64 プロセスの混合モードのデバッグはサポートされていません。 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9965f83feed7d12ac48aefdd248aebfc9a524473
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>IA64 プロセスの混合モードのデバッグはサポートされていません。
Visual Studio では、IA64 プロセスでマネージ コードとネイティブ コードの混合モードのデバッグはサポートされていません。 つまり、デバッグ中にマネージ コードからネイティブ コードにステップ インすることや、ネイティブ コードからマネージ コードにステップ インすることはできません。  
  
### <a name="workarounds"></a>問題回避  
  
-   マネージ コードとネイティブ コードを個別のデバッガー セッション内でデバッグする。  
  
     または  
  
     次の手順に示すように、混合コードを 32 ビット プロセスとしてデバッグする。  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>プラットフォームを 32 ビットに変更するには (Visual Basic または C#)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、をクリックして、**プロパティ**ショートカット メニュー。  
  
2.  プロパティ ページ をクリックして、**コンパイル**または**デバッグ** タブ。  
  
3.  をクリックして**プラットフォーム**とプラットフォームの一覧から [x86] を選択します。  
  
     Visual Basic コンパイラおよび C# コンパイラの既定では、どの CPU 上でも実行されるコードが生成されます。 64 ビット コンピューター上では、これらのバイナリは 64 ビット プロセスとして実行されます。 で、32 ビット プロセスを実行する必要がありますを選択する**Win32**ではなく、 **AnyCPU**です。  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>プラットフォームを 32 ビットに変更するには (C/C++)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、をクリックして、**プロパティ**ショートカット メニュー。  
  
2.  プロパティ ページで、をクリックして**プラットフォーム**プラットフォームの一覧から [Win32] を選択し、  
  
## <a name="see-also"></a>関連項目  
 [64 ビット アプリケーションをデバッグする](../debugger/debug-64-bit-applications.md)