---
title: カスタム ツール |Microsoft Docs
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
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dce865af4dd1f8498dcd697b53abdb8608abed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793426"
---
# <a name="custom-tools"></a>カスタム ツール
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*カスタム ツール*ツールをプロジェクト内の項目に関連付けるし、ファイルを保存するたびに、そのツールを実行することができます。 特定のカスタム ツールとも呼ば*単一ファイル ジェネレーター*、データから、またはその逆にコードを生成する翻訳者を実装するために頻繁に使用されます。 たとえば、単一ファイル ジェネレーターの作成[!INCLUDE[csprcs](../../includes/csprcs-md.md)]と[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].settings および .resx ファイルからコードをソースします。 生成されたソース コードは、.settings および .resx ファイル内のデータへの厳密に型指定されたアクセスを提供します。 [!INCLUDE[csprcs](../../includes/csprcs-md.md)]と[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]; のカスタム ツールをサポートするプロジェクトの種類[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクトの種類はありません。 独自のプロジェクトの種類には、カスタム ツールもサポートできます。  
  
 カスタム ツールを実装するコンポーネントが登録されているは、`IVsSingleFileGenerator`インターフェイス。  
  
 カスタム ツールの関連付けられている、`ProjectItem`インターフェイス オブジェクト、およびデザイナーおよびエディターのようなものです。 カスタム ツールで表されるファイルでは、`ProjectItem`入力し、ファイル名がによって提供される新しいファイルを書き込むだけ、`DefaultExtension`メソッド。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)  
 使用する方法について説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>カスタム ツールを実装するインターフェイス。  
  
 [プロジェクトの既定の名前空間の決定](../../misc/determining-the-default-namespace-of-a-project.md)  
 使用されている言語に基づいて正しい名前空間を決定する方法について説明します。  
  
 [単一ファイル ジェネレーターの登録](../../extensibility/internals/registering-single-file-generators.md)  
 カスタム ツールのすべてのレジストリ エントリについて説明します。  
  
 [ビジュアル デザイナーへのタイプの公開](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 どのようにプロジェクト システム サポートを提供アクセスが生成されるクラスと型をビジュアル デザイナーの一時的なポータブル実行可能 (PE) ファイルをについて説明します。  
  
 [プロジェクト項目のプロパティの保存](../../extensibility/persisting-the-property-of-a-project-item.md)  
 プロジェクト ファイル内のソース ファイルの作成者など、プロジェクト項目のプロパティを永続化する方法を示しています。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 詳細について説明します、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>、1 つの入力ファイルをコンパイルまたはプロジェクトに追加できる単一の出力ファイルに変換します。  
  
 <xref:EnvDTE.ProjectItem>  
 について説明します、`ProjectItem`インターフェイスで、プロジェクト内の項目を表します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 詳細について説明します、`DefaultExtension`メソッドで、出力ファイル名に指定されているファイル名拡張子を取得します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクトの拡張](../../extensibility/extending-projects.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロジェクトおよびソリューションを使用してコード ファイルとリソース ファイルを編成する方法、またソース管理を実装する方法について説明します。

