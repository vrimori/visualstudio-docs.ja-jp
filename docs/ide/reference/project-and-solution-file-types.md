---
title: プロジェクト ファイルとソリューション ファイルの種類
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3786d6f38e4f87aa05a51b0a6112613bda65e56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
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

C++ プロジェクトでのファイルの種類について詳しくは、「[File Types Created for Visual C++ Projects](/cpp/ide/file-types-created-for-visual-cpp-projects)」(Visual C++ プロジェクトに対して作成されるファイルの種類) をご覧ください。

## <a name="see-also"></a>関連項目

- [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)