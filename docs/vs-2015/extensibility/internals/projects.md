---
title: プロジェクト |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb67c01732f5347e13c09146379d2b79298d198d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236055"
---
# <a name="projects"></a>プロジェクト
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio で、プロジェクトは、開発者は、ソース コード ファイルと含まれるその他のリソースを分類に使用するコンテナー**ソリューション エクスプ ローラー**します。 通常、プロジェクトは、ソース コード ファイルおよびビットマップ ファイルなどのリソースへの参照を格納するファイル (たとえば、c# プロジェクトの .csproj ファイル) です。 プロジェクトの整理、ビルド、デバッグ、およびソース コードを配置するように、Web サービスとデータベース、およびその他のリソースへの参照します。 Vspackage は、次の 3 つの主な方法で、Visual Studio プロジェクト システムを拡張できます。*プロジェクトの種類*、*プロジェクトのサブタイプ*、および*カスタム ツール*します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 *プロジェクトの種類*プログラミング言語など、プロジェクトの新しい種類のサポートを追加します。 たとえば、Visual Studio をサポートする各言語が独自のプロジェクトの種類と、IronPython の統合サンプルには、IronPython の言語のプロジェクトの種類が含まれています。 品目のビルド、デバッグ、展開されるとに表示される方法をカスタマイズする c# または Visual Basic 以外の言語のプロジェクトの種類を作成する必要があります**ソリューション エクスプ ローラー**します。 詳細については、次を参照してください。[プロジェクトの種類](../../extensibility/internals/project-types.md)します。  
  
 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)  
 *プロジェクトのサブタイプ*はプロジェクトの種類に基づいており、プロジェクトのビルド、デバッグ、および配置方法をカスタマイズするために使用できます。 Visual Studio スマート デバイス プロジェクトでのプロジェクト サブタイプを使用します。デプロイをカスタマイズするには、新しくビルドされたプログラムを開発用コンピューターからターゲット デバイスにコピーします。 C# および Visual Basic プロジェクトの種類はプロジェクトのサブタイプの基礎として使用できます。C++ プロジェクトの種類ことはできません。 独自のプロジェクトの種類は、プロジェクトのサブタイプの基礎としても使用できます。 詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
 [Web プロジェクト](../../extensibility/internals/web-projects.md)  
 Web プロジェクトは、さらに Web アプリケーションの作成について説明します。  
  
 [新しいプロジェクトの生成: 内部、パート 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)と[新しいプロジェクトの生成: 内部、パート 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 新しいプロジェクトを作成するときに実際の処理について説明します。  
  
 [VSSDK のサンプル](../../misc/vssdk-samples.md)  
 プロジェクトとソリューションを処理する VSSDK のサンプルについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Studio SDK の内部](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Visual Studio 機能拡張のさまざまな側面をについて説明します。

