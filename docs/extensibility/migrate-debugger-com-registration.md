---
title: "64 ビット デバッガー COM クラスの登録の移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 19ce2d4cc1ff92240529f35f42845778ded49fdf
ms.lasthandoff: 03/07/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64 ビット デバッガー COM クラスの登録を移行します。

(Regasm、regsvr32 を使用して、レジストリへの直接書き込み、)、HKEY_CLASSES_ROOT に COM クラスを登録し、msvsmon.exe (リモート デバッガー) に読み込まれるデバッガー拡張機能には、HKEY_CLASSES_ROOT を記述せずに msvsmon には、この登録を提供することはようになりました。 これは、従来の .NET デバッガー式エバリュエーターまたは msvsmon.exe プロセスで読み込むように構成されているデバッグ エンジンに影響します。

## <a name="msvsmon-comclass-def"></a>msvsmon-def comclass

この手法を使用するには、msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64) の横にある *.msvsmon comclass-def.json ファイルを追加します。

いずれかの管理、登録する msvsmon-def comclass ファイルの例と&1; つのネイティブ クラスを次に示します。

ファイル名: MyCompany.MyExample.msvsmon comclass def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```

