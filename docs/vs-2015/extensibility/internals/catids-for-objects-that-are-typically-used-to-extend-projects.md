---
title: プロジェクトの拡張に通常使用されるオブジェクトの Catid |Microsoft Docs
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
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f9daee3e188aeb098961aa6631f7901efad2aa8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224056"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>プロジェクトの拡張に通常使用されるオブジェクトの CATID
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

次の表に、拡張に使用される Catid`Project`と`ProjectItem`オートメーション オブジェクトに対する[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]、 [!INCLUDE[csprcs](../../includes/csprcs-md.md)]、および[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクト。 これらの Catid は VSLangProj.olb で定義されます。  
  
## <a name="listing-of-catids"></a>Catid を一覧表示します。  
  
|名前|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|  
  
## <a name="visual-basic-catids"></a>Visual Basic の Catid  
 次の表に、拡張に使用される Catid[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]のオブジェクトを参照します。 すべてで定義されている VSLangProj.olb します。  
  
|名前|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|  
  
## <a name="visual-c-catids"></a>Visual c# の Catid  
 次の Catid を拡張に使用できる[!INCLUDE[csprcs](../../includes/csprcs-md.md)]のオブジェクトを参照します。 すべてで定義されている VSLangProj.olb します。  
  
|名前|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|  
  
## <a name="c-catids"></a>C++ の Catid  
 次[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクト システムのタイプ ライブラリで公開の Catid [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET 2003年がこれらのプロジェクト オブジェクトを拡張するときに、コードに含まれるとします。 これらの Catid を以降のリリースでタイプ ライブラリに含まれます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
|名前|GUID|  
|----------|----------|  
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 次のコード例では、コードでこれらの Catid をプログラミングする方法を示します。  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 次[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクト システムでのタイプ ライブラリ Catid は公開されませんも[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].NET 2003年これらのプロジェクト オブジェクトを拡張するときに、コードに含める必要があるとします。 これらの Catid でのみ使用できます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].NET 2003年以降のリリースで利用できない、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
|名前|GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|  
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 次のコード例では、コードでこれらの Catid をプログラミングする方法を示します。  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Guid、[!INCLUDE[csprcs](../../includes/csprcs-md.md)]と[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]プロジェクトの種類は、次の表に表示されます。  
  
|プロジェクトの種類|GUID|  
|------------------|----------|  
|[!INCLUDE[csprcs](../../includes/csprcs-md.md)]|{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}|  
|[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]|{F184B08F-C81C-45F6-A57F-5ABD9991F28F}|  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)

