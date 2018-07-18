---
title: プロジェクト |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2ca4edabcee9f561dea51ea4b579ce194d13fa8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131011"
---
# <a name="projects"></a>プロジェクト
Visual Studio で、プロジェクトはソース コード ファイルおよびに表示されるその他のリソースを整理する開発者が使用できるコンテナー**ソリューション エクスプ ローラー**です。 通常、プロジェクトは、ソース コード ファイルおよびビットマップ ファイルなどのリソースへの参照を格納するファイル (たとえば、c# プロジェクトの .csproj ファイル) です。 プロジェクトの整理、ビルド、デバッグ、およびソース コードを配置することができます、Web サービスとデータベース、およびその他のリソースへの参照します。 Vspackage は、3 つの主な方法で Visual Studio プロジェクト システムを拡張することができます:*プロジェクトの種類*、*プロジェクトのサブタイプ*、および*カスタム ツール*です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 *プロジェクトの種類*プログラミング言語など、プロジェクトの新しい種類のサポートを追加します。 たとえば、Visual Studio でサポートされている各言語が独自のプロジェクトの種類には、IronPython の統合サンプルには、IronPython 言語のプロジェクトの種類が含まれています。 方法項目は、ビルド、デバッグ、展開、およびに表示をカスタマイズする c# または Visual Basic 以外の言語のプロジェクトの種類を作成する必要があります**ソリューション エクスプ ローラー**です。 詳細については、次を参照してください。[プロジェクトの種類](../../extensibility/internals/project-types.md)です。  
  
 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)  
 *プロジェクトのサブタイプ*はプロジェクトの種類に基づいており、プロジェクトがビルド、デバッグ、および配置方法をカスタマイズするために使用できます。 Visual Studio は、スマート デバイス プロジェクトとプロジェクトのサブタイプを使用します。配置の新しくビルドされたプログラムを開発用コンピューターからターゲット デバイスにコピーして、カスタマイズします。 C# および Visual Basic プロジェクトの種類はプロジェクトのサブタイプの基礎として使用できます。C++ プロジェクトの種類ことはできません。 独自のプロジェクトの種類は、プロジェクト サブタイプの基礎としても使用できます。 詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)です。  
  
 [Web プロジェクト](../../extensibility/internals/web-projects.md)  
 Web プロジェクトは、さらに Web アプリケーションの作成について説明します。  
  
 [新しいプロジェクトの生成: フードのパート 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)と[新しいプロジェクトの生成: フードの下部、パート 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 新しいプロジェクトを作成するときに実際の処理について説明します。  
  
 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)  
 プロジェクトとソリューションを処理する VSSDK のサンプルが含まれています。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Studio SDK の内部](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Visual Studio 拡張機能のさまざまな側面をについて説明します。