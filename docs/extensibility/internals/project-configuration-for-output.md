---
title: プロジェクトの出力の構成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a02e331484abf2ef1450493d2ea1bdddaabe82bd
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901185"
---
# <a name="project-configuration-for-output"></a>出力のためのプロジェクト構成
すべての構成には、一連の実行可能ファイルまたはリソース ファイルなどの出力項目を生成するビルド プロセスをサポートできます。 これらの出力項目は、ユーザーにプライベートであり実行可能ファイル (.exe、.dll、.lib) とソース ファイル (.idl、.h ファイル) のような出力の関連する型のリンクのグループに配置することができます。  
  
 出力項目を利用できる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>メソッドを列挙し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>メソッド。 出力項目をグループ化する場合は、プロジェクトを実装する必要がありますも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>インターフェイス。  
  
 実装することによって、コンストラクトが開発した`IVsOutputGroup`使用量に応じて出力をグループにプロジェクトを使用します。 たとえば、DLL は、そのプログラム データベース (PDB) と共にグループ化する可能性があります。  
  
> [!NOTE]
>  PDB ファイルにデバッグ情報が含まれていて、.dll または .exe を構築するときに、' デバッグ情報の生成 ' オプションが指定されているときに作成されます。 .Pdb ファイルは通常のデバッグ プロジェクト構成にのみ生成されます。  
  
 プロジェクトは、場合でも、グループ内に含まれる出力の数は構成で異なる場合があります、同じ数のサポートされる構成ごとにグループを返す必要があります。 たとえば、プロジェクト Matt の DLL には、デバッグ構成を mattd.dll と mattd.pdb を含めるが、のみ matt.dll を製品版構成に含めることがあります。  
  
 グループも同じ情報を持つ識別子などの正規名、表示名、およびグループについては、構成、プロジェクト内で。 この整合性は、デプロイしパッケージ化する場合でも、構成の変更を引き続き使用できます。  
  
 グループには、キーの出力を指す何か意味のあるパッケージのショートカットを許可することもできます。 グループのサイズに関する仮定は行われませんので、任意のグループを特定の構成では空にする可能性があります。 構成では、各グループのサイズ (出力の数) は、同じ構成の別のグループのサイズを異なっていてもかまいません。 別の構成で同じグループのサイズと異なることができます。  
  
 ![出力グループ グラフィック](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
出力グループ  
  
 主な用途、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg>インターフェイスが構築、デプロイ、管理オブジェクトをデバッグおよびプロジェクト グループの出力に自由に許可するへのアクセスを提供することです。 このインターフェイスの使用に関する詳細については、次を参照してください。[プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)します。  
  
 前の図でグループが構築されたため (bD.exe または b.exe) の構成で出力キーを持つユーザーは組み込みにショートカットを作成し、ショートカットが展開された構成に関係なく動作するかを確認します。 グループ ソースには、出力のキーはありませんので、ユーザーへのショートカットを作成できません。 キーの出力を持つグループのデバッグ ビルド小売グループ作成されない場合は、不適切な実装の場合は。 \Inboxes\smsbkup.box\smsbkup.ctl、する場合は、構成では、出力が含まれていないグループと、結果として、キー ファイルがない、し、そのグループに出力が含まれて他の構成キー ファイルことはできません。 インストーラー エディターでは、前提としていますが正規名と、グループの表示名とキーのファイルが存在する変更されない構成に基づく。  
  
 プロジェクトに場合、`IVsOutputGroup`ことをパッケージをデプロイしたりしたくないはないグループにその出力を配置するための十分な。 出力を実装することによって通常列挙ができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>をすべてのグループ化に関係なく、構成の出力を返すメソッド。  
  
 詳細については、の実装を参照してください。`IVsOutputGroup`でカスタム プロジェクト サンプル[プロジェクトの MPF](https://github.com/tunnelvisionlabs/MPFProj10)します。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [ビルドするためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)