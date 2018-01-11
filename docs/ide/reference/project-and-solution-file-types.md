---
title: "プロジェクト ファイルとソリューション ファイルの種類 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
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
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d05b7b5f1510777c758998572e78757c47148fa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="project-and-solution-file-types"></a>プロジェクト ファイルとソリューション ファイルの種類

Visual Studio は、さまざまな種類のファイルをサポートしています。 特定のインストールでは、インストールされるコンポーネントによってサポートされるファイルの種類が決まります。 このトピックでは、いくつかの標準的なインストールでサポートされるソリューション ファイルとプロジェクト ファイルの種類について説明します。

## <a name="solution-files-sln-and-suo"></a>ソリューション ファイル (.sln および .suo)

Visual Studio では、ソリューションの設定を格納するために、2 種類のファイル (.sln および .suo) を使用します。 これらのファイルはまとめてソリューション ファイルと呼ばれており、ソリューション エクスプローラーがファイル管理用のグラフィカル インターフェイスを表示するのに必要な情報が格納されています。

|拡張子|name|説明|
|---------------|----------|-----------------|
|.sln|Visual Studio ソリューション|プロジェクト、プロジェクト項目、およびソリューション項目としてまとめます。|
|.suo|ソリューション ユーザー オプション|Visual Studio で行ったブレークポイントなどのユーザー レベルのカスタマイズを追跡します。|

## <a name="project-files"></a>プロジェクト ファイル

プロジェクトにはさまざまな種類のファイルを含めることができます。 たとえば、C# コード ファイルの拡張子は **.cs**、C++ ファイルの拡張子は **.cpp** です。 リソースは **.resx** ファイルに、XAML は **.xaml** ファイルに格納されます。 [App.config](../../ide/managing-application-settings-dotnet.md) ファイルには、アプリケーション コードに含めない方がよいアプリケーション情報 (接続文字列など) が含まれています。

C++ プロジェクトのファイルの種類については、「[Visual C++ プロジェクトに対して作成されるファイルの種類](/cpp/ide/file-types-created-for-visual-cpp-projects)」と「[Unicode in Microsoft Foundation Class Library](/cpp/mfc/unicode-in-mfc)」(Microsoft Foundation Class ライブラリの Unicode) を参照してください。

## <a name="see-also"></a>関連項目

[ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)