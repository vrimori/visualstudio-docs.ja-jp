---
title: 'デバッグの準備: Visual C プロジェクトの種類 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 64d49d799c0ec0b3845a262c248d2438572ecd5d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478188"
---
# <a name="debugging-preparation-visual-c-project-types"></a>デバッグの準備 : Visual C++ のプロジェクト
ここでは、[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] プロジェクト テンプレートで作成された基本的なプロジェクトの種類をデバッグする方法について説明します。  
  
 出力として Dll を作成するプロジェクトの種類に分類された注[DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)一般的な機能を共有しているためです。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 [プロパティの推奨設定](#BKMK_Recommended_Property_Settings)  
  
 [Win32 プロジェクト](#BKMK_Win32_Projects)  
  
-   [C または C++ の Win32 アプリケーションをデバッグするには](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [デバッグ構成を手動で設定するには](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Windows フォーム アプリケーション (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> プロパティの推奨設定  
 プロパティによっては、すべてのアンマネージ デバッグ シナリオで同じように設定する必要があります。 プロパティの推奨設定を以下に示します。 ここに記載されていない設定は、アンマネージ プロジェクトの種類によって異なる場合があります。 詳細については、次を参照してください[C++ デバッグ構成のプロジェクト設定。](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>構成プロパティ&#124;C/C++&#124;最適化ノード  
  
|プロパティ名|設定|  
|-------------------|-------------|  
|**Optimization**|設定**無効 (/0 d)。** 最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。 プログラムには、最適化されたコードにだけ現れるバグが見つかったら場合、することができます、この設定を有効にはそのコードに示すように、**逆アセンブル**ウィンドウは、ソースで表示される内容に一致が最適化されたソースから生成windows です。 また、ステップなどの他の機能が正常に動作しない場合もあります。|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>構成プロパティ&#124;リンカー&#124;デバッグ ノード  
  
|プロパティ名|設定|  
|-------------------|-------------|  
|**デバッグ情報を生成します。**|常にこのオプションに設定する必要があります**はい (/debug)** デバッグ シンボルとデバッグに必要なファイルを作成します。 アプリケーションを稼働するときは、このオプションをオフに設定できます。|  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Win32 プロジェクト  
 Win32 アプリケーションは、C または C++ で記述される従来の Windows プログラムです。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、この種類のアプリケーションを簡単にデバッグできます。  
  
 Win32 アプリケーションには、MFC アプリケーションと ATL プロジェクトが含まれます。 これらは Windows API を使用します。MFC や ATL を使用することはありますが、共通言語ランタイム (CLR: Common Language Runtime) は使用しません。 ただし、CLR を使用するマネージ コードを呼び出すことはできます。  
  
 次の手順では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内から Win32 プロジェクトをデバッグする方法を説明します。 Win32 アプリケーションをデバッグするもう 1 つの方法では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部でアプリケーションを起動してアタッチします。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> C または C++ の Win32 アプリケーションをデバッグするには  
  
1.  Visual Studio でプロジェクトを開きます。  
  
2.  **デバッグ**] メニューの [選択**開始**です。  
  
3.  説明した手法を使用してデバッグ[デバッガーの基礎](../debugger/debugger-basics.md)です。  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> デバッグ構成を手動で設定するには  
  
1.  **ビュー**  メニューのをクリックして**プロパティ ページ**です。  
  
2.  クリックして、**構成プロパティ**ノードになっていない場合  
  
3.  選択**全般**の値を設定し、**出力**行を**デバッグ**です。  
  
4.  開く、 **C/C++** ノード、および選択**全般**です。  
  
     **デバッグ**デバッグ コンパイラによって生成される情報の種類を指定する行。 選択した可能性があります値を含める**プログラム データベース (/Zi)** または**編集と続行 (/ZI) 用のプログラム データベース**です。  
  
5.  選択**最適化**、し、、**最適化**行で、**無効 (/0 d)** ドロップダウン リストからです。  
  
     最適化されたコードは、生成された命令がソース コードと直接対応していないため、デバッグが困難です。 プログラムで、最適化されたコード内だけに現れるバグが見つかった場合は、この設定を有効にできます。[逆アセンブル] ウィンドウに表示されるコードは最適化されたソースから生成されているため、ソース ウィンドウに表示されるコードとは一致しない可能性があります。 ステップ実行などの機能で、ブレークポイントや実行ポイントが正しく表示されない場合があります。  
  
6.  開く、**リンカー**ノード、および選択**デバッグ**です。 最初の**生成**行で、 **はい (/debug)** ドロップダウン リストからです。 デバッグ時には、必ずこのオプションを設定する必要があります。  
  
 詳細については、次を参照してください。[C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)です。  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows フォーム アプリケーション (.NET)  
 **Windows フォーム アプリケーション (.NET)** テンプレートを作成、 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Windows フォーム アプリケーションです。 詳細については、「 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
 この種のアプリケーションを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でデバッグする作業は、マネージ Windows フォーム アプリケーションのデバッグ作業に似ています。  
  
 プロジェクト テンプレートを使用して Windows フォーム プロジェクトを作成する場合、デバッグ構成とリリース構成に必要な設定は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって自動的に作成されます。 かどうか、必要に応じて変更できますでこれらの設定、 **\<プロジェクト名 > プロパティ ページ** ダイアログ ボックス。 詳細については、次を参照してください。[デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)です。  
  
 詳細については、次を参照してください。 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)です。  
  
 Windows フォーム アプリケーションをデバッグするもう 1 つの方法では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部でアプリケーションを起動してアタッチします。 詳細については、次を参照してください。[実行中のプログラムまたは複数のプログラムへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。  
  
 [このトピックの内容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [実行中のプログラムまたは複数のプログラムへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)   
 [方法: Windows アプリケーション プロジェクトの作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)