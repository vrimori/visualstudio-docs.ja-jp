---
title: 'デバッグの準備: Visual C プロジェクトの種類 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 592232277dd8eda337bf90e6df114c2a03e75c4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538378"
---
# <a name="debugging-preparation-visual-c-project-types"></a>デバッグの準備 : Visual C++ のプロジェクト
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッグの準備: Visual C++ プロジェクトの種類](https://docs.microsoft.com/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)します。  
  
ここでは、[!INCLUDE[vcprvc](../includes/vcprvc-md.md)] プロジェクト テンプレートで作成された基本的なプロジェクトの種類をデバッグする方法について説明します。  
  
 出力として Dll を作成するプロジェクトの種類に分類された注[DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)共有している一般的な機能のため。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 [プロパティの推奨設定](#BKMK_Recommended_Property_Settings)  
  
 [Win32 プロジェクト](#BKMK_Win32_Projects)  
  
-   [C または C++ の Win32 アプリケーションをデバッグするには](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [デバッグ構成を手動で設定するには](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Windows フォーム アプリケーション (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> プロパティの推奨設定  
 プロパティによっては、すべてのアンマネージ デバッグ シナリオで同じように設定する必要があります。 プロパティの推奨設定を以下に示します。 ここに記載されていない設定は、アンマネージ プロジェクトの種類によって異なる場合があります。 詳細については、次を参照してください[C++ デバッグ構成のプロジェクトの設定。](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>構成プロパティ&#124;C/C++&#124;最適化ノード  
  
|プロパティ名|設定|  
|-------------------|-------------|  
|**Optimization**|設定**無効 (/0 d)。** 最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。 プログラムが最適化されたコードにだけ現れるバグを発見した場合は、この設定を有効しますが、コードに示すように、**逆アセンブル**ウィンドウは、ソースに表示される内容が一致しないがあります最適化されたソースから生成windows とします。 また、ステップなどの他の機能が正常に動作しない場合もあります。|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>構成プロパティ&#124;リンカー&#124;デバッグ ノード  
  
|プロパティ名|設定|  
|-------------------|-------------|  
|**デバッグ情報を生成します。**|常にこのオプションを設定する必要があります**はい (/debug)** デバッグ シンボルとデバッグに必要なファイルを作成します。 アプリケーションを稼働するときは、このオプションをオフに設定できます。|  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Win32 プロジェクト  
 Win32 アプリケーションは、C または C++ で記述される従来の Windows プログラムです。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、この種類のアプリケーションを簡単にデバッグできます。  
  
 Win32 アプリケーションには、MFC アプリケーションと ATL プロジェクトが含まれます。 これらは Windows API を使用します。MFC や ATL を使用することはありますが、共通言語ランタイム (CLR: Common Language Runtime) は使用しません。 ただし、CLR を使用するマネージド コードを呼び出すことはできます。  
  
 次の手順では、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 内から Win32 プロジェクトをデバッグする方法を説明します。 Win32 アプリケーションをデバッグするもう 1 つの方法では、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の外部でアプリケーションを起動してアタッチします。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> C または C++ の Win32 アプリケーションをデバッグするには  
  
1.  Visual Studio でプロジェクトを開きます。  
  
2.  **デバッグ**] メニューの [選択**開始**します。  
  
3.  説明した手法を使用してデバッグ[デバッガーの基本事項](../debugger/debugger-basics.md)します。  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> デバッグ構成を手動で設定するには  
  
1.  **ビュー**  メニューのをクリックして**プロパティ ページ**します。  
  
2.  をクリックして、**構成プロパティ**開くことになっていないノード  
  
3.  選択**全般**の値を設定し、**出力**行**デバッグ**。  
  
4.  開く、 **C/C++** ノード、および選択**全般**します。  
  
     **デバッグ**すると、コンパイラによって生成されるデバッグ情報の種類を指定する行。 選択した可能性があります値を含める**プログラム データベース (/Zi)** または**編集と続行 (/ZI) 用のプログラム データベース**します。  
  
5.  選択**最適化**、し、**最適化**行で、**無効 (/0 d)** ドロップダウン リストから。  
  
     最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。 プログラムで、最適化されたコード内だけに現れるバグが見つかった場合は、この設定を有効にできます。[逆アセンブル] ウィンドウに表示されるコードは最適化されたソースから生成されているため、ソース ウィンドウに表示されるコードとは一致しない可能性があります。 ステップ実行などの機能で、ブレークポイントや実行ポイントが正しく表示されない場合があります。  
  
6.  開く、**リンカー**ノード、および選択**デバッグ**します。 最初の**生成**行で、**はい (/debug)** ドロップダウン リストから。 デバッグ時には、必ずこのオプションを設定する必要があります。  
  
 詳細については、次を参照してください。[C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)します。  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows フォーム アプリケーション (.NET)  
 **Windows フォーム アプリケーション (.NET)** テンプレートを作成、 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Windows フォーム アプリケーションです。 詳細については、「 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
 この種のアプリケーションを [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でデバッグする作業は、マネージド Windows フォーム アプリケーションのデバッグ作業に似ています。  
  
 プロジェクト テンプレートを使用して Windows フォーム プロジェクトを作成する場合、デバッグ構成とリリース構成に必要な設定は [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって自動的に作成されます。 かどうか、必要に応じて変更できますでこれらの設定、 **\<プロジェクト名 > プロパティ ページ** ダイアログ ボックス。 詳細については、次を参照してください。[デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)します。  
  
 詳細については、次を参照してください。 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)します。  
  
 Windows フォーム アプリケーションをデバッグするもう 1 つの方法では、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の外部でアプリケーションを起動してアタッチします。 詳細については、次を参照してください。[実行中のプログラムまたは複数のプログラムへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [実行中のプログラムまたは複数のプログラムへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)   
 [方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)



