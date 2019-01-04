---
title: カスタム ドキュメント プロパティの概要
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: bd76957844008975f67c6c1cb504aa0388b9e91b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936894"
---
# <a name="custom-document-properties-overview"></a>カスタム ドキュメント プロパティの概要

ドキュメント レベルのプロジェクトをビルドするときに Visual Studio には、プロジェクト内のドキュメントに 2 つのカスタム プロパティが追加されます。\_AssemblyLocation と\_AssemblyName。 文書を開くと、これらのカスタム ドキュメント プロパティを Microsoft Office アプリケーションによって確認されます。 ドキュメントに存在する場合、アプリケーションの読み込み、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]カスタマイズを開始します。 詳細については、次を参照してください。 [Visual Studio での Office のアーキテクチャ ソリューション](../vsto/architecture-of-office-solutions-in-visual-studio.md)します。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

このプロパティは、インターフェイスでの Office ソリューション ローダー コンポーネントの CLSID を格納、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。 CLSID 値は、4E3C66D5-58 D 4-491E-A7D4-64AF99AF6E8B です。 この値を変更しないでください。

## <a name="assemblylocation"></a>\_AssemblyLocation

このプロパティには、カスタマイズの詳細については、配置マニフェストを提供する文字列が含まれています。 マニフェストの詳細については、次を参照してください。 [Office ソリューションでのアプリケーションと展開マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)します。

 The_AssemblyLocation プロパティの値は、ソリューションの展開方法に応じて、異なる形式を持つことができます。

- _AssemblyLocation プロパティの形式が、ソリューションを発行して Web サイト、UNC パス、または、CD または USB ドライブからインストールする場合*DeploymentManifestPath*|*SolutionID*します。 次の文字列は、例を示します。

     file://deployserver/MyShare/ExcelWorkbook1.vsto | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- _AssemblyLocation プロパティが、形式で実行されているまたは Visual Studio からソリューションをデバッグする場合*DeploymentManifestName*|*SolutionID*| vstolocal します。 次の文字列は、例を示します。

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  *SolutionID*は GUID ですが、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ソリューションを識別するために使用します。 *SolutionID*プロジェクトをビルドするときに自動的に生成されます。 **Vstolocal**用語をすることを示します、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]アセンブリをドキュメントと同じフォルダーから読み込まれる必要があります。

## <a name="see-also"></a>関連項目

- [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)
- [Office ソリューションにおけるアプリケーションと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [方法: ClickOnce を使用して、Office ソリューションを発行します。](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [方法: 作成し、カスタム ドキュメント プロパティの変更](../vsto/how-to-create-and-modify-custom-document-properties.md)
