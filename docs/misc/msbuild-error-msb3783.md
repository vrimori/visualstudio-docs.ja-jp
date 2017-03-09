---
title: "MSBuild エラー MSB3783 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.ResolveSDKReference.MaxPlatformVersionLessThanTargetPlatformVersion"
ms.assetid: 847fc96e-73d3-4aa5-927a-ef8cebc8d3f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3783
**MSB3783: TargetPlatformVersion の値 "{2}" 未満の値 "{1}" を持つ属性 MaxPlatformVersion が存在するため、"{0}" SDK を解決できません。**  
  
 MSBuild では、プロジェクトの依存関係がプロジェクトの対象となっているプラットフォームと互換性がない場合に、このエラーが発生します。  互換性のない依存関係を使用すると、実行時にエラーや予期しないアプリの動作が発生する可能性があります。  
  
### プロジェクト参照に関するこのエラーを解決するには  
  
1.  [!INCLUDE[win81](../debugger/includes/win81_md.md)] ストア プロジェクトを対象とする Visual Basic、C\#、C\+\+、JavaScript の各プロジェクトでは、[!INCLUDE[win8](../debugger/includes/win8_md.md)] を対象とする C\+\+ Windows ストア プロジェクトを参照できません。これは、実行時の問題が発生するためです。  アプリ内のいずれかのプロジェクトが [!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象としており、アプリが C\+\+ Windows ストア プロジェクトで構成されている場合、次の手順を実行する必要があります。  
  
2.  アプリ内のすべてのプロジェクトを [!INCLUDE[win81](../debugger/includes/win81_md.md)] に再ターゲットします。  これを行うには、アプリ内の各プロジェクトを右クリックし、**\[Windows 8.1 に再ターゲット\]** を選択します。次に、**\[プロジェクトとソリューションの変更をレビュー\]** ダイアログで **\[OK\]** をクリックします。  
  
3.  C\+\+ Windows ストア プロジェクトに依存する Visual Basic、C\#、JavaScript の各プロジェクトを右クリックし、**\[参照の追加\]** を選択して、**\[Windows\]** タブに移動します。次に **\[Extensions\] \(拡張機能\)** サブタブで、**\[Microsoft Visual C\+\+ ランタイム パッケージ v11.0\]** をオフに、**\[Microsoft Visual C\+\+ ランタイム パッケージ v12.0\]** をオンにし、**\[OK\]** をクリックします。  
  
4.  [!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象としている Visual Basic、C\#、JavaScript の各 Windows ストア プロジェクトは、[!INCLUDE[win8](../debugger/includes/win8_md.md)] を対象としている Visual Basic や C\# の各 Windows ストア プロジェクトを参照できますが、その [!INCLUDE[win8](../debugger/includes/win8_md.md)] ストア プロジェクトが [!INCLUDE[win81](../debugger/includes/win81_md.md)] で廃止された API を使用していない必要があります。  [!INCLUDE[win81](../debugger/includes/win81_md.md)] プロジェクトから参照したときに [!INCLUDE[win8](../debugger/includes/win8_md.md)] ストア プロジェクトが引き続き目的どおりに動作するかどうかを確認するには、「[Windows ストア アプリの Windows 8.1 への移植](http://msdn.microsoft.com/library/windows/apps/dn263113.aspx)」を参照してください。  
  
     [!INCLUDE[win8](../debugger/includes/win8_md.md)] ストア プロジェクトは、[!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象とする Windows ストア プロジェクトやバイナリに依存することはできません。  
  
### 拡張 SDK 参照に関するこのエラーを解決するには  
  
1.  [!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象とする Visual Basic、C\#、C\+\+、JavaScript の各 Windows ストア プロジェクトは、Microsoft Visual C\+\+ ランタイム パッケージ v11.0 に依存する拡張 SDK を参照できません。これは、実行時の問題が発生するためです。  拡張 SDK が Microsoft Visual C\+\+ ランタイム パッケージ v11.0 に依存しているかどうかを調べるには、まず新しい C\# Windows ストア プロジェクトを作成します。そのプロジェクトを右クリックし、**\[参照の追加\]** を選択して、**\[Windows\]** タブに移動します。次に **\[Extensions\] \(拡張機能\)** サブタブで拡張 SDK を選択し、**\[参照マネージャー\]** の右側のウィンドウに **\[Microsoft.VCLibs, version \= 11.0\] \(Microsoft.VCLibs, バージョン \= 11.0\)** が依存関係として示されているかどうかを確認します。  
  
     [!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象としている Visual Basic、C\#、JavaScript の各 Windows ストア プロジェクトは、Microsoft Visual C\+\+ ランタイム パッケージ v11.0 に依存していない拡張 SDK を参照できます。ただし、その拡張 SDK が [!INCLUDE[win81](../debugger/includes/win81_md.md)] で廃止された API を使用していない必要があります。  [!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象としているストア プロジェクトから拡張 SDK を参照できるかどうかを確認するには、その拡張 SDK の販売元のサイトを調べてください。  
  
     アプリで参照している拡張 SDK がサポートされていないことがわかった場合、次の手順を実行する必要があります。  
  
2.  エラーの原因となっているプロジェクトの名前を確認します。  プロジェクトのターゲット プラットフォームはプロジェクト名の横にあるかっこ内に表示されます。  たとえば、"**MyProjectName \(Windows 8.1\)**" は、プロジェクト MyProjectName がプラットフォーム バージョン [!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象としていることを意味します。  
  
3.  サポートされていない拡張 SDK の販売元のサイトにアクセスして、プロジェクトのターゲット プラットフォームのバージョンと互換性のある依存関係を持つ拡張 SDK のバージョンをインストールします。  
  
4.  以前にインストールした拡張 SDK が他の拡張 SDK に依存している場合、その依存関係に関連する販売元のサイトにアクセスして、プロジェクトのターゲット プラットフォームのバージョンと互換性のある依存関係のバージョンをインストールします。  
  
    > [!NOTE]
    >  プロジェクトが [!INCLUDE[win81](../debugger/includes/win81_md.md)] を対象としており、以前にインストールした拡張 SDK が Microsoft Visual C\+\+ ランタイム パッケージに依存している場合、Windows 8.1 と互換性のある Microsoft Visual C\+\+ ランタイム パッケージのバージョンは v12.0 になります。このバージョンは [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] と共にインストールされます。  
  
    > [!NOTE]
    >  以前にインストールされた拡張 SDK が他の拡張 SDK に依存しているかどうかを調べるには、Visual Studio を再起動し、新しい C\# Windows ストア プロジェクトを作成します。そのプロジェクトを右クリックし、**\[参照の追加\]** を選択して、**\[Windows\]** タブに移動します。次に **\[Extensions\] \(拡張機能\)** サブタブで拡張 SDK を選択し、**\[参照マネージャー\]** の右側のウィンドウを確認します。  依存関係がある場合は、そのウィンドウに表示されます。  
  
5.  Visual Studio を再起動し、アプリを開きます。  
  
6.  エラーの原因となっているプロジェクトを右クリックし、\[**参照の追加**\] \(プロジェクトが Visual Basic、C\#、JavaScript の場合\) または \[**参照**\] \(プロジェクトが C\+\+ の場合\) を選択します。  C\+\+ プロジェクトの場合は、さらに \[新しい参照の追加\] ボタンをクリックします。  
  
7.  **\[Windows\]** タブをクリックし、**\[拡張機能\]** サブタブをクリックします。  以前の拡張 SDK の横にあるチェック ボックスをオフにし、新しい拡張 SDK の横にあるチェック ボックスをオンにします。  **\[OK\]** をクリックします。