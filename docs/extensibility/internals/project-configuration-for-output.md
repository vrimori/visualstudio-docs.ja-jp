---
title: "出力のプロジェクト構成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクトの構成、出力"
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 出力のプロジェクト構成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

すべての構成には、実行可能ファイルまたはリソース ファイルなどの出力項目を作成するビルド プロセスのセットをサポートできます。 これらの出力項目はユーザーに対してプライベートであり、出力実行可能ファイル \(.exe、.dll、.lib\) とソース ファイル \(.idl、.h ファイル\) などの関連する型をリンクしているグループに配置することができます。  
  
 出力項目が利用できるを通じて、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> メソッドを列挙し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> メソッドです。 出力アイテムをグループ化する場合は、プロジェクトが実装する必要も、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> インターフェイスです。  
  
 コンストラクトが実装することによって開発された `IVsOutputGroup` プロジェクトの使用状況に応じてグループの出力にできます。 たとえば、DLL は、そのプログラム データベース \(PDB\) と共にグループ化する可能性があります。  
  
> [!NOTE]
>  PDB ファイルには、デバッグ情報が含まれていて、.dll または .exe を作成するときにデバッグ情報の生成\] オプションが指定されたときに作成されます。 .Pdb ファイルは通常、デバッグ プロジェクト構成にのみ生成されます。  
  
 場合でも、グループ内に含まれる出力の数は、構成を異なる場合があります、プロジェクトは同じグループをサポートしている各構成の数を返す必要があります。 たとえば、プロジェクト Matt の DLL には、デバッグ構成を mattd.dll と mattd.pdb を含めるが、のみ matt.dll を製品版の構成に含めることがあります。  
  
 グループも同じ情報を持つ識別子などの正規名、表示名、およびグループについては、構成、プロジェクト内で。 この一貫性は、展開とパッケージ化する場合でも、構成の変更の操作を続行できます。  
  
 グループには、キーの出力へのショートカットを意味のあるポイントをパッケージ化できるようにすることもできます。 グループのサイズに関する前提条件は行われませんは、任意のグループが特定の構成で空にすることがあります。 構成では、各グループのサイズ \(出力の数\) は、同じ構成の別のグループのサイズと異なる設定できます。 別の構成で同じグループのサイズと異なることができます。  
  
 ![出力グループ グラフィック](../../extensibility/internals/media/vsoutputgroups.png "vsOutputGroups")  
出力グループ  
  
 主な用途、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> インターフェイスは、構築、展開し管理オブジェクトをデバッグおよびプロジェクトに許可するグループの出力に自由にアクセスできるようにします。 このインターフェイスの使用方法の詳細については、次を参照してください。 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)します。  
  
 上の図にそのための構成 \(bD.exe または b.exe\) 間で出力キーを持つグループの作成、ユーザーは組み込みにショートカットを作成し、ショートカットが展開された構成に関係なく動作するかを確認します。 グループのソースには、出力のキーはないので、ユーザーへのショートカットを作成できません。 キーの出力を持つグループのデバッグ ビルド小売グループ作成されない場合を実装が不適切になります。 それに依存して、次を任意の構成に含まれていない出力、グループがある場合や、その結果、なしのキー ファイル、そのグループには出力を含むその他の構成はキー ファイル。 インストーラー エディターと、正規名と、グループの表示名とキー ファイルの存在は変化しません構成にします。  
  
 プロジェクトに注意してください、 `IVsOutputGroup` いるパッケージまたは展開したくあまりせんはないグループにその出力を配置するだけで十分です。 出力も列挙できる通常実装することによって、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> すべてのグループ化に関係なく、構成の出力を返すメソッド。  
  
 詳細については、の実装を参照してください。 `IVsOutputGroup` でカスタム プロジェクト サンプルに [プロジェクトの MPF](http://mpfproj12.codeplex.com)します。  
  
## 参照  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)