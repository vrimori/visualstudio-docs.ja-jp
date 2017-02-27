---
title: "プロジェクト ファイルとソリューション ファイルの種類 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "File Properties.CopyToOutputDirectory"
  - "File Properties.CustomToolNamespace"
  - "File Properties.FileName"
  - "File Properties.FullPath"
  - "File Properties.BuildAction"
  - "File Properties.CustomTool"
  - "FileProperties"
helpviewer_keywords: 
  - ".sln ファイル"
  - ".suo ファイル"
  - "拡張, ファイルの種類"
  - "ファイルの拡張子"
  - "ファイルの拡張子, Visual Studio"
  - "ファイルの種類"
  - "ファイルの種類, Visual Studio"
  - "sln ファイル"
  - "ソリューション ファイル"
  - "ソリューション, ソリューション ファイル"
  - "suo ファイル"
  - "Visual Studio, ファイルの種類と拡張子"
ms.assetid: 0ba5007b-465d-4efa-b1e4-f0ee68527649
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# プロジェクト ファイルとソリューション ファイルの種類
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は、多くの種類のファイルをサポートします。  特定のインストールでは、インストールされるコンポーネントによってサポートされるファイルの種類が決まります。  このトピックでは、いくつかの標準的なインストールでサポートされるソリューション ファイルとプロジェクト ファイルの種類について説明します。  その他のファイルの種類の詳細については、それぞれの種類のファイル名拡張子を使用して検索してください。  
  
## ソリューション ファイル \(.sln および .suo\)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] では、ソリューション固有の設定を格納するために、2 種類のファイル \(.sln および .suo\) を使用します。  これらのファイルはまとめてソリューション ファイルと呼ばれており、ソリューション エクスプローラーがファイル管理用のグラフィカル インターフェイスを表示するのに必要な情報が格納されています。  これらのファイルよって、開発タスクに戻るたびに環境を気にする必要はなくなり、プロジェクトと最終的な目標に集中できます。  
  
|拡張子|名前|説明|  
|---------|--------|--------|  
|.sln|[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソリューション|プロジェクト、プロジェクト項目、およびソリューション項目としてまとめます。|  
|.suo|ソリューション ユーザー オプション|Visual Studio で行ったブレークポイントなどのユーザー レベルのカスタマイズを追跡します。|  
  
## プロジェクト ファイル  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] では、プロジェクト固有の情報を格納するために、さまざまなファイル形式を使用します。  詳細については、次のヘルプ トピックを参照してください。  
  
 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]  
 [Visual C\+\+ プロジェクトに対して作成されるファイルの種類](/visual-cpp/ide/file-types-created-for-visual-cpp-projects)  
  
 [Visual C\+\+ プロジェクトの作成および管理](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)  
  
 [Unicode](/visual-cpp/mfc/unicode-in-mfc)  
  
## 参照  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)