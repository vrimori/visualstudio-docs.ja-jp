---
title: "カスタム ツール |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7589c9a2aedf987af79689e8babccb554fbb4ccc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tools"></a>カスタム ツール
*カスタム ツール*ツールをプロジェクト内の項目に関連付けるし、ファイルを保存するたびに、そのツールを実行できます。 特定のカスタム ツールとも呼ば*単一ファイル ジェネレーター*、データから、その逆のコードを生成する翻訳者を実装するのには頻繁に使用します。 たとえば、単一ファイル ジェネレーターを作成[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].settings および .resx ファイルからコードをソースします。 生成されたソース コードでは、.settings、.resx ファイル内のデータへの厳密に型指定されたアクセスを提供します。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]; のカスタム ツールをサポートするプロジェクトの種類[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクトの種類がありません。 独自のプロジェクトの種類には、カスタム ツールもサポートできます。  
  
 カスタム ツールは、登録されているコンポーネントを実装する、`IVsSingleFileGenerator`インターフェイスです。  
  
 カスタム ツールが関連付けられている、`ProjectItem`インターフェイス オブジェクト、およびデザイナーおよびエディターのようなものです。 カスタム ツールで表されるファイルでは、`ProjectItem`として入力し、ファイル名がによって提供される新しいファイルに書き込み、`DefaultExtension`メソッドです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)  
 使用する方法について説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>カスタム ツールを実装するインターフェイスです。  
  
 [単一ファイル ジェネレーターの登録](../../extensibility/internals/registering-single-file-generators.md)  
 カスタム ツールのすべてのレジストリ エントリについて説明します。  
  
 [ビジュアル デザイナーへのタイプの公開](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 プロジェクト システムを提供する方法のサポート アクセスが生成されるクラスと型をビジュアル デザイナーの一時的なポータブル実行可能 (PE) ファイルをについて説明します。  
  
 [プロジェクト項目のプロパティの保存](../../extensibility/persisting-the-property-of-a-project-item.md)  
 プロジェクト ファイル内のソース ファイルの作成者など、プロジェクト項目のプロパティを永続化する方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 詳細について説明、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>、コンパイルまたはプロジェクトに追加できる 1 つの出力ファイルに 1 つの入力ファイルを変換します。  
  
 <xref:EnvDTE.ProjectItem>  
 について説明します、`ProjectItem`インターフェイスで、プロジェクトのアイテムを表します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 詳細について説明、`DefaultExtension`メソッドで、出力ファイル名に指定されているファイル名拡張子を取得します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクトの拡張](../../extensibility/extending-projects.md)  
 使用する方法について説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトおよびソリューションのコード ファイルとリソース ファイル、およびソース管理を実装する方法を整理します。