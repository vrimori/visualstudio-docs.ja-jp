---
title: プロジェクトの出力の構成 |Microsoft ドキュメント
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
ms.openlocfilehash: d9bb68812ed9988c9ed18174231ead24f91fcf9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-for-output"></a>出力用のプロジェクトの構成
すべての構成には、一連の実行可能ファイルまたはリソース ファイルなどの出力項目を生成するビルド プロセスをサポートできます。 これらの出力項目はユーザーにプライベートであり、出力実行可能ファイル (.exe、.dll、.lib) とソース ファイル (.idl、.h ファイル) などの関連する型をリンクしているグループに配置することができます。  
  
 出力項目が利用できるを通じて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>メソッドを列挙し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>メソッドです。 出力項目をグループ化する場合は、プロジェクトが実装する必要も、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>インターフェイスです。  
  
 コンストラクトが実装することによって開発された`IVsOutputGroup`使用量に従って出力をグループにプロジェクトを使用します。 たとえば、DLL は、プログラム データベース (PDB) とグループ化する可能性があります。  
  
> [!NOTE]
>  PDB ファイルには、デバッグ情報が含まれています。 および、.dll または .exe を構築するときにデバッグ情報の生成 ' オプションが指定されたときに作成されます。 .Pdb ファイルは通常、デバッグ プロジェクト構成にのみ生成されます。  
  
 プロジェクトは、グループ内に含まれる出力の数は変化する構成から構成する場合でも同じ数のグループをサポートしている各構成を返す必要があります。 たとえば、プロジェクト Matt の DLL には、デバッグ構成で mattd.dll と mattd.pdb を含めるが、小売構成 matt.dll にのみ含めることがあります。  
  
 グループも同じ情報を持つ識別子などの正規名、表示名、およびグループについては、構成、プロジェクト内で。 この一貫性は、配置とパッケージ化する場合でも、構成の変更操作を続行できます。  
  
 グループには、キーの出力へのショートカットを意味のあるポイントをパッケージ化できるようにすることもできます。 任意のグループは、ので、グループのサイズに関する前提条件は行われません、特定の構成で空にすることがあります。 任意の構成内の各グループのサイズ (出力の数) は、同じ構成の別のグループのサイズと別にすることはできます。 別の構成で同じグループのサイズと異なることができます。  
  
 ![出力グループ グラフィック](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
出力グループ  
  
 主な用途、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg>インターフェイスは、ビルド、配置、管理オブジェクトをデバッグおよびグループの出力を自由にプロジェクトを許可するへのアクセスを提供することです。 このインターフェイスの使用に関する詳細については、次を参照してください。[プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)です。  
  
 前の図でための構成 (bD.exe または b.exe) 間で出力キーを持つグループの作成、ユーザーが組み込みへのショートカットを作成して、ショートカットが展開された構成に関係なく動作するを把握します。 グループのソースには、出力キーはないので、ユーザーへのショートカットを作成できません。 キーの出力を持つグループのデバッグ ビルド小売グループ作成されない場合は、実装が正しくないことになります。 従う、その後、任意の構成が含まれていない出力、グループがある場合と、結果として、キー ファイルがない、し、そのグループには出力を含むその他の構成のキー ファイルことはできません。 インストーラー エディターと正規名と、グループの表示名とキーのファイルの存在を変更しないことの構成に基づいてします。  
  
 プロジェクトに注意してください、`IVsOutputGroup`ことにしないようにするパッケージまたは展開がないグループにその出力を配置するだけで十分です。 出力も列挙できる通常実装することによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>をすべてのグループ化に関係なく、構成の出力を返すメソッド。  
  
 詳細については、の実装を参照してください。`IVsOutputGroup`でカスタム プロジェクト サンプル[プロジェクトの MPF](http://mpfproj12.codeplex.com)です。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)