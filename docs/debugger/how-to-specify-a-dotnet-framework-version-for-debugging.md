---
title: "方法 : デバッグで .NET Framework のバージョンを指定する | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".NET Framework, 指定 (デバッグ用にバージョンを)"
  - "デバッグ [Visual Studio], 指定 (.NET Framework のバージョンを)"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : デバッグで .NET Framework のバージョンを指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] デバッガーでは、Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の現在のバージョンだけでなく、古いバージョンのデバッグもサポートしています。  Visual Studio からアプリケーションを起動すると、デバッグしているアプリケーションの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョンは正しく識別されます。  アプリケーションが既に実行されていて、**\[アタッチ先\]** を使用する場合、古いバージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] が識別されないこともあります。  この場合、次のようなエラー メッセージが出力されます。  
  
 "アプリケーションが使用しようとしている Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンに関してデバッガーが不適切な想定を行っています。"  
  
 このような場合はまれですが、使用するデバッガーのバージョンを指定するには、レジストリ キーを設定します。  
  
### デバッグで .NET Framework のバージョンを指定するには  
  
1.  コンピューターにインストールされている .NET Framework のバージョンを確認するには、Windows\\Microsoft.NET\\Framework ディレクトリを探します。  バージョン番号は次のようになります。  
  
     `V1.1.4322`  
  
     正しいバージョン番号を確認し、メモしておきます。  
  
2.  **レジストリ エディター** \(regedit\) を起動します。  
  
3.  **レジストリ エディター**で、\[HKEY\_LOCAL\_MACHINE\] フォルダーを開きます。  
  
4.  HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} に移動します。  
  
     このキーが存在しない場合、HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine を右クリックし、**\[新しいキー\]** をクリックします。  新しいキーに `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` と名前を付けます。  
  
5.  {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} に移動し、**\[名前\]** 列を確認して、CLRVersionForDebugging キーを探します。  
  
    1.  このキーが存在しない場合、{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} を右クリックし、**\[新規\] \- \[文字列値\]** をクリックします。  新しい文字列値を右クリックし、**\[名前の変更\]** をクリックして、「`CLRVersionForDebugging`」と入力します。  
  
6.  **\[CLRVersionForDebugging\]** をダブルクリックします。  
  
7.  **\[文字列の編集\]** ボックスの **\[値\]** ボックスに、.NET Framework のバージョン番号を入力します。  たとえば、「V1.1.4322」などです。  
  
8.  **\[OK\]** をクリックします。  
  
9. **レジストリ エディター**を閉じます。  
  
     それでもデバッグの開始時にエラー メッセージが表示される場合は、レジストリに正しいバージョン番号が入力されていることを確認します。  また、Visual Studio でサポートされている [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを使用していることを確認します。  デバッガーは、現在のバージョンおよび以前のバージョンの .NET Framework と互換性がありますが、将来のバージョンとの上位互換性はない可能性があります。  
  
## 参照  
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)