---
title: カスタム ドキュメント プロパティの概要
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85dfe077f73a26eadf173197de2ca514ff44679
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="custom-document-properties-overview"></a>カスタム ドキュメント プロパティの概要

Visual Studio がプロジェクト内のドキュメントを 2 つのカスタム プロパティを追加、ドキュメント レベルのプロジェクトをビルドすると: \_AssemblyLocation と\_AssemblyName。 ユーザーがドキュメントを開いたときに、Microsoft Office アプリケーションがこれらのカスタム ドキュメント プロパティを確認します。 ドキュメントに存在する場合、アプリケーションの読み込み、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]カスタマイズを開始します。 詳細については、次を参照してください。 [Visual Studio での Office のアーキテクチャ ソリューション](../vsto/architecture-of-office-solutions-in-visual-studio.md)です。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

このプロパティは、Office ソリューション ローダー コンポーネントでのインターフェイスの CLSID を含む、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。 CLSID 値は、4E3C66D5-58 D 4-491E-A7D4-64AF99AF6E8B です。 この値を変更しないでください。

## <a name="assemblylocation"></a>\_AssemblyLocation

このプロパティには、カスタマイズの詳細については、配置マニフェストを提供する文字列が含まれています。 マニフェストの詳細については、次を参照してください。[アプリケーション マニフェストおよび配置マニフェスト Office ソリューションにおける](../vsto/application-and-deployment-manifests-in-office-solutions.md)です。

 The_AssemblyLocation プロパティの値は、ソリューションが配置された方法に応じて、さまざまな形式を持つことができます。

- _AssemblyLocation プロパティは、の形式でパブリッシュする場合、ソリューションは、Web サイト、UNC パス、または、CD ドライブまたは USB ドライブからインストールする、 *DeploymentManifestPath*|*ソリューション Id*です。 次の文字列は、例を示します。

     file://deployserver/MyShare/ExcelWorkbook1.vsto | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- _AssemblyLocation プロパティが、形式で実行されているまたは、Visual Studio からソリューションをデバッグする場合*DeploymentManifestName*|*ソリューション Id*| vstolocal です。 次の文字列は、例を示します。

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 *ソリューション Id* guid を[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]を使用して、ソリューションを識別します。 *ソリューション Id*プロジェクトをビルドするときに自動的に生成します。 **Vstolocal**用語をすることを示します、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]アセンブリをドキュメントと同じフォルダーからアンロードする必要があります。

## <a name="see-also"></a>関連項目

- [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)
- [アプリケーション マニフェストと配置マニフェストの Office ソリューション](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [方法: ClickOnce を使用して Office ソリューションの発行](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [方法: を作成し、カスタム ドキュメント プロパティの変更](../vsto/how-to-create-and-modify-custom-document-properties.md)
