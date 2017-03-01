---
title: "プロジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 842bef303d7a3211b8711920ef6cec357a876f8a
ms.lasthandoff: 02/22/2017

---
# <a name="projects"></a>プロジェクト
Visual Studio で、プロジェクトは、開発者は、ソース コード ファイルおよびに表示されるその他のリソースを分類に使用するコンテナー**ソリューション エクスプ ローラー**します。 通常、プロジェクトは、ソース コード ファイルおよびビットマップ ファイルなどのリソースへの参照を格納するファイル (たとえば、c# プロジェクトの .csproj ファイル) です。 プロジェクトを整理、ビルド、デバッグ、およびソース コードを配置することができます、Web サービスとデータベース、およびその他のリソースへの参照します。 VSPackages は&3; つの主な方法で Visual Studio プロジェクト システムを拡張することができます:*プロジェクトの種類*、*プロジェクトのサブタイプ*、および*カスタム ツール*します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 *プロジェクトの種類*新しい種類のプログラミング言語などのプロジェクトのサポートを追加します。 たとえば、Visual Studio でサポートされる言語ごとは独自のプロジェクトの種類を持ち、IronPython の統合サンプルには、IronPython の言語のプロジェクトの種類が含まれています。 どの項目はビルド、デバッグ、展開、およびに表示をカスタマイズする c# または Visual Basic 以外の言語のプロジェクトの種類を作成する必要があります**ソリューション エクスプ ローラー**します。 詳細については、次を参照してください。[プロジェクトの種類](../../extensibility/internals/project-types.md)します。  
  
 [プロジェクトのサブタイプ](../../extensibility/internals/project-subtypes.md)  
 *プロジェクトのサブタイプ*はプロジェクトの種類に基づいており、プロジェクトのビルド、デバッグ、および配置方法をカスタマイズするために使用できます。 Visual Studio は、スマート デバイス プロジェクトとプロジェクトのサブタイプを使用します。展開をカスタマイズするには、新たに構築したプログラムを開発用コンピューターからターゲット デバイスにコピーします。 C# および Visual Basic プロジェクトの種類はプロジェクトのサブタイプの基礎として使用できます。C++ プロジェクトの種類ことはできません。 独自のプロジェクトの種類は、プロジェクトのサブタイプの基礎としても使用できます。 詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
 [Web プロジェクト](../../extensibility/internals/web-projects.md)  
 Web プロジェクトは、さらに Web アプリケーションの作成について説明します。  
  
 [新しいプロジェクトの生成: 実際のところ、第&1; 部](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)と[新しいプロジェクトの生成: 実際のところ、第&2; 部](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 新しいプロジェクトを作成するときに実際の処理について説明します。  
  
 [VSSDK のサンプル](../../misc/vssdk-samples.md)  
 プロジェクトとソリューションを処理する、VSSDK のサンプルについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Studio SDK 内](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Visual Studio 拡張機能のさまざまな側面をについて説明します。
