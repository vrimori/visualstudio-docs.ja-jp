---
title: VSTU によって作成されるプロジェクト ファイルのカスタマイズ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: ef11a6585d741fd28de918d4fa2a81f1eb927b43
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533504"
---
# <a name="customize-project-files-created-by-vstu"></a>VSTU によって作成されるプロジェクト ファイルのカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[カスタマイズ プロジェクト ファイル VSTU によって作成される](https://docs.microsoft.com/visualstudio/cross-platform/customize-project-files-created-by-vstu)します。  
  
  
Visual Studio Tools for Unity は、プロジェクト ファイルの生成時に Unity スタイルのコールバックを提供します。 `VisualStudioIntegration.ProjectFileGeneration` イベントに登録し、プロジェクト ファイルが再生成されるたびに、それを変更します。  
  
## <a name="demonstrates"></a>使用例  
 Visual Studio Tools for Unity によって生成された Visual Studio プロジェクト ファイルをカスタマイズする方法について示します。  
  
## <a name="example"></a>例  
  
```csharp  
using System;  
using System.IO;  
using System.Linq;  
using System.Text;  
using System.Xml.Linq;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class ProjectFileHook  
{  
    // necessary for XLinq to save the xml project file in utf8  
    class Utf8StringWriter : StringWriter  
    {  
        public override Encoding Encoding  
        {  
            get { return Encoding.UTF8; }  
        }  
    }  
  
    static ProjectFileHook()  
    {  
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>  
        {  
            // parse the document and make some changes  
            var document = XDocument.Parse(content);  
            document.Root.Add(new XComment("FIX ME"));  
  
            // save the changes using the Utf8StringWriter  
            var str = new Utf8StringWriter();  
            document.Save(str);  
  
            return str.ToString();  
        };  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [例: ログのコールバック](../cross-platform/share-the-unity-log-callback-with-vstu.md)

