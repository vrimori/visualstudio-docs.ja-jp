---
title: "x64 プロセスの混合モード デバッグは、4 より前の Microsoft .NET Framework バージョンを使用している場合にはサポートされません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# x64 プロセスの混合モード デバッグは、4 より前の Microsoft .NET Framework バージョンを使用している場合にはサポートされません。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

バージョンが 4 より前の .NET Framework では、x64 プロセスの混合モード デバッグはサポートされません。  つまり、デバッグ中にマネージ コードからネイティブ コードにステップ インすることや、ネイティブ コードからマネージ コードにステップ インすることはできません。  
  
### 問題回避  
  
-   Microsoft .NET Framework 4 以降を使用するようにプロジェクトを更新する。  
  
     または  
  
     マネージ コードとネイティブ コードを個別のデバッガー セッション内でデバッグする。  
  
     または  
  
     次の手順に示すように、混合コードを 32 ビット プロセスとしてデバッグする。  
  
### プラットフォームを 32 ビットに変更するには \(Visual Basic または C\#\)  
  
1.  **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  プロパティ ページで、**\[コンパイル\]** タブまたは **\[デバッグ\]** タブをクリックします。  
  
3.  **\[プラットフォーム\]** をクリックし、プラットフォームの一覧から \[x86\] を選択します。  
  
     Visual Basic コンパイラおよび C\# コンパイラの既定では、どの CPU 上でも実行されるコードが生成されます。  64 ビット コンピューター上では、これらのバイナリは 64 ビット プロセスとして実行されます。  32 ビット プロセスとして実行するには、**\[Any CPU\]** でなく **\[Win32\]** を選択する必要があります。  
  
### プラットフォームを 32 ビットに変更するには \(C\/C\+\+\)  
  
1.  **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  プロパティ ページで **\[プラットフォーム\]** をクリックし、プラットフォームの一覧から \[Win32\] を選択します。  
  
### このエラーを解決するには  
  
-   「[Setting Up SQL Debugging](http://msdn.microsoft.com/ja-jp/3db09e68-edcc-42de-9c22-4e97cfd55ab3)」を参照してください。  
  
## 参照  
 [64 ビット アプリケーションをデバッグする](../debugger/debug-64-bit-applications.md)