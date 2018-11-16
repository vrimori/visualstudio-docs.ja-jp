---
title: IA64 プロセスの混合モードのデバッグはサポートされていません。 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12623f2692735b8a6ec31a4ecaa7bfc0b07e9364
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806465"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>IA64 プロセスの混合モードのデバッグはサポートされていません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio では、IA64 プロセスでマネージド コードとネイティブ コードの混合モードのデバッグはサポートされていません。 つまり、デバッグ中にマネージド コードからネイティブ コードにステップ インすることや、ネイティブ コードからマネージド コードにステップ インすることはできません。  
  
### <a name="workarounds"></a>問題回避  
  
-   マネージド コードとネイティブ コードを個別のデバッガー セッション内でデバッグする。  
  
     または  
  
     次の手順に示すように、混合コードを 32 ビット プロセスとしてデバッグする。  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>プラットフォームを 32 ビットに変更するには (Visual Basic または C#)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**ショートカット メニュー。  
  
2.  [プロパティ ページ] でをクリックして、**コンパイル**または**デバッグ**タブ。  
  
3.  クリックして**プラットフォーム**プラットフォームの一覧から x86 を選択します。  
  
     Visual Basic コンパイラおよび C# コンパイラの既定では、どの CPU 上でも実行されるコードが生成されます。 64 ビット コンピューター上では、これらのバイナリは 64 ビット プロセスとして実行されます。 選択する必要があります、32 ビット プロセスで実行する**Win32**ではなく、 **AnyCPU**します。  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>プラットフォームを 32 ビットに変更するには (C/C++)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**ショートカット メニュー。  
  
2.  [プロパティ ページ] でクリックして**プラットフォーム**プラットフォームの一覧から Win32 を選択します。  
  
## <a name="see-also"></a>関連項目  
 [64 ビット アプリケーションをデバッグする](../debugger/debug-64-bit-applications.md)



