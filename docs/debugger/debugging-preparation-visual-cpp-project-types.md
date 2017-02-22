---
title: "デバッグの準備 : Visual C++ のプロジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "C++"
helpviewer_keywords: 
  - "デバッグ ビルド, プロジェクト設定"
  - "デバッグ [C++]"
  - "プロジェクト テンプレート, デバッグ"
  - "Visual C++ プロジェクト, デバッグ"
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# デバッグの準備 : Visual C++ のプロジェクト
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] プロジェクト テンプレートで作成された基本的なプロジェクトの種類をデバッグする方法について説明します。  
  
 出力として DLL を作成するプロジェクトは、共通する特徴があるため [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md) にグループ化されています。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 [プロパティの推奨設定](#BKMK_Recommended_Property_Settings)  
  
 [Win32 プロジェクト](#BKMK_Win32_Projects)  
  
-   [C または C++ の Win32 アプリケーションをデバッグするには](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [デバッグ構成を手動で設定するには](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Windows フォーム アプリケーション (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> プロパティの推奨設定  
 プロパティによっては、すべてのアンマネージ デバッグ シナリオで同じように設定する必要があります。  プロパティの推奨設定を以下に示します。  ここに記載されていない設定は、アンマネージ プロジェクトの種類によって異なる場合があります。  詳細については、「[C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)」を参照してください。  
  
### 構成プロパティ &#124; C\/C\+\+ &#124; 最適化ノード  
  
|プロパティ名|設定値|  
|------------|---------|  
|**最適化**|**\[無効 \(\/0d\)\]** に設定します。 最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。  プログラムで、最適化されたコード内だけに現れるバグが見つかった場合は、この設定を有効にできます。**逆アセンブル** ウィンドウに表示されるコードは最適化されたソースから生成されているため、ソース ウィンドウに表示されるコードとは一致しない可能性があります。  また、ステップなどの他の機能が正常に動作しない場合もあります。|  
  
### 構成プロパティ &#124; リンカー &#124; デバッグ ノード  
  
|プロパティ名|設定値|  
|------------|---------|  
|**\[デバッグ情報の生成\]**|このオプションは、デバッグ シンボルとデバッグに必要なファイルを作成するために常に **\[はい \(\/DEBUG\)\]** に設定する必要があります。  アプリケーションを稼働するときは、このオプションをオフに設定できます。|  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Win32 プロジェクト  
 Win32 アプリケーションは、C または C\+\+ で記述される従来の Windows プログラムです。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、この種類のアプリケーションを簡単にデバッグできます。  
  
 Win32 アプリケーションには、MFC アプリケーションと ATL プロジェクトが含まれます。  これらは Windows API を使用します。MFC や ATL を使用することはありますが、共通言語ランタイム \(CLR: Common Language Runtime\) は使用しません。  ただし、CLR を使用するマネージ コードを呼び出すことはできます。  
  
 次の手順では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内から Win32 プロジェクトをデバッグする方法を説明します。  Win32 アプリケーションをデバッグするもう 1 つの方法では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部でアプリケーションを起動してアタッチします。  詳細については、「[実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> C または C\+\+ の Win32 アプリケーションをデバッグするには  
  
1.  Visual Studio でプロジェクトを開きます。  
  
2.  **\[デバッグ\]** メニューの **\[開始\]** をクリックします。  
  
3.  「[デバッガーの基本事項](../debugger/debugger-basics.md)」で説明されている方法でデバッグします。  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> デバッグ構成を手動で設定するには  
  
1.  **\[表示\]** メニューの **\[プロパティ ページ\]** をクリックします。  
  
2.  **\[構成プロパティ\]** ノードが開いていない場合は、ノードをクリックして開きます。  
  
3.  **\[全般\]** をクリックし、**\[出力\]** 行の値を **\[Debug\]** に設定します。  
  
4.  **\[C\/C\+\+\]** ノードを開き、**\[全般\]** をクリックします。  
  
     **\[デバッグ情報の形式\]** 行で、コンパイラで生成するデバッグ情報の種類を指定します。  選択できる値は、**\[プログラム データベース \(\/Zi\)\]**、**\[エディット コンティニュ用プログラム データベース \(\/ZI\)\]** などです。  
  
5.  **\[最適化\]** をクリックし、**\[最適化\]** 行で、ドロップダウン リストの **\[無効 \(\/0d\)\]** をクリックします。  
  
     最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。  プログラムで、最適化されたコード内だけに現れるバグが見つかった場合は、この設定を有効にできます。\[逆アセンブル\] ウィンドウに表示されるコードは最適化されたソースから生成されているため、ソース ウィンドウに表示されるコードとは一致しない可能性があります。  ステップ実行などの機能で、ブレークポイントや実行ポイントが正しく表示されない場合があります。  
  
6.  **\[リンカー\]** ノードを開き、**\[デバッグ\]** をクリックします。  最初の **\[デバッグ情報の生成\]** 行で、ドロップダウン リストの **\[はい \(\/DEBUG\)\]** をクリックします。  デバッグ時には、必ずこのオプションを設定する必要があります。  
  
 詳細については、「[C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)」を参照してください。  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows フォーム アプリケーション \(.NET\)  
 **Windows フォーム アプリケーション \(.NET\)** テンプレートを使用して [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] Windows フォーム アプリケーションを作成できます。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
 この種のアプリケーションを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でデバッグする作業は、マネージ Windows フォーム アプリケーションのデバッグ作業に似ています。  
  
 プロジェクト テンプレートを使用して Windows フォーム プロジェクトを作成する場合、デバッグ構成とリリース構成に必要な設定は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって自動的に作成されます。  必要に応じて、これらの設定を **\[\<プロジェクト名\> プロパティ ページ\]** ダイアログ ボックスで変更できます。  詳細については、「[デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)」を参照してください。  
  
 詳細については、「[C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)」を参照してください。  
  
 Windows フォーム アプリケーションをデバッグするもう 1 つの方法では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部でアプリケーションを起動してアタッチします。  詳細については、「[実行中のプログラムまたは複数のプログラムへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## 参照  
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [実行中のプログラムまたは複数のプログラムへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)