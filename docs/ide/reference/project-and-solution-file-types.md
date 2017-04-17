---
title: "プロジェクト ファイルとソリューション ファイルの種類 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- suo files
- file types, Visual Studio
- file extensions
- solutions, solution files
- solution files
- .sln files
- Visual Studio, file types and extensions
- extensions, file types
- sln files
- .suo files
- file extensions, Visual Studio
- file types
ms.assetid: 0ba5007b-465d-4efa-b1e4-f0ee68527649
caps.latest.revision: 19
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: b8f389deae83848893e59daec16630c911925f19
ms.lasthandoff: 04/05/2017

---
# <a name="project-and-solution-file-types"></a>プロジェクト ファイルとソリューション ファイルの種類
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は、多くの種類のファイルをサポートします。 特定のインストールでは、インストールされるコンポーネントによってサポートされるファイルの種類が決まります。 このトピックでは、いくつかの標準的なインストールでサポートされるソリューション ファイルとプロジェクト ファイルの種類について説明します。 その他のファイルの種類の詳細については、それぞれの種類のファイル名拡張子を使用して検索してください。  
  
## <a name="solution-files-sln-and-suo"></a>ソリューション ファイル (.sln および .suo)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] では、ソリューション固有の設定を格納するために、2 種類のファイル (.sln および .suo) を使用します。 これらのファイルはまとめてソリューション ファイルと呼ばれており、ソリューション エクスプローラーがファイル管理用のグラフィカル インターフェイスを表示するのに必要な情報が格納されています。 これらのファイルよって、開発タスクに戻るたびに環境を気にする必要はなくなり、プロジェクトと最終的な目標に集中できます。  
  
|拡張子|名前|説明|  
|---------------|----------|-----------------|  
|.sln|[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソリューション|プロジェクト、プロジェクト項目、およびソリューション項目としてまとめます。|  
|.suo|ソリューション ユーザー オプション|Visual Studio で行ったブレークポイントなどのユーザー レベルのカスタマイズを追跡します。|  
  
## <a name="project-files"></a>プロジェクト ファイル  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] では、プロジェクト固有の情報を格納するために、さまざまなファイル形式を使用します。 詳細については、次のヘルプ トピックを参照してください。  
  
 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]  
 [Visual C++ プロジェクトに対して作成されるファイルの種類](/cpp/ide/file-types-created-for-visual-cpp-projects)  
  
 [Visual C++ プロジェクトの作成と管理](/cpp/ide/creating-and-managing-visual-cpp-projects)  
  
 [Unicode](/cpp/mfc/unicode-in-mfc)  
  
## <a name="see-also"></a>関連項目  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)
