---
title: "混合モード デバッグは、Microsoft .NET Framework 2.0 以上を使用している場合にのみサポートされます | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_to_old"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 混合モード デバッグは、Microsoft .NET Framework 2.0 以上を使用している場合にのみサポートされます
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

2.0 より前のバージョンの Microsoft .NET Framework では、64 ビット プロセスの混合モード デバッグはサポートされません。  つまり、デバッグ中にマネージ コードからネイティブ コードにステップ インすることや、ネイティブ コードからマネージ コードにステップ インすることはできません。  
  
 この問題を回避するには、次の操作を実行します。  
  
-   Microsoft .NET Framework 2.0 または 3.0 のどちらかを使用するようにプロジェクトを更新する。  
  
-   マネージ コードとネイティブ コードを個別のデバッガー セッション内でデバッグする。  
  
-   次の手順に示すように、混合コードを 32 ビット プロセスとしてデバッグする。  
  
### オペレーティング システムを 32 ビットに変更するには \(Visual Basic または C\#\)  
  
1.  **ソリューション エクスプローラー**でプロジェクトを右クリックし、ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
2.  プロパティ ページで、**\[コンパイル\]** タブまたは **\[デバッグ\]** タブをクリックします。  
  
3.  **\[プラットフォーム\]** をクリックし、プラットフォームの一覧から **\[x86\]** を選択します。  
  
     Visual Basic コンパイラおよび C\# コンパイラの既定では、どの CPU 上でも実行されるコードが生成されます。  64 ビット コンピューター上では、これらのバイナリは 64 ビット プロセスとして実行されます。  32 ビット プロセスとして実行するには、**\[Any CPU\]** でなく **\[Win32\]** を選択する必要があります。  
  
### オペレーティング システムを 32 ビットに変更するには \(C\/C\+\+\)  
  
1.  **ソリューション エクスプローラー**でプロジェクトを右クリックし、ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
     プロパティ ページで **\[プラットフォーム\]** をクリックし、プラットフォームの一覧から **\[Win32\]** を選択します。  
  
### このエラーを解決するには  
  
-   「[Setting Up SQL Debugging](http://msdn.microsoft.com/ja-jp/3db09e68-edcc-42de-9c22-4e97cfd55ab3)」を参照してください。  
  
## 参照  
 [64 ビット アプリケーションをデバッグする](../debugger/debug-64-bit-applications.md)