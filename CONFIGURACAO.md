# 📋 Configuração do Projeto - Prettier, ESLint e VSCode

## ✅ Configurações Realizadas

### 1. **Prettier** `.prettierrc`
- ✅ Espaçamento de **2 tabs** por padrão
- ✅ Sem ponto-e-vírgula (`semi: false`)
- ✅ Aspas simples (`singleQuote: true`)
- ✅ Vírgula final em objetos/arrays (`trailingComma: "all"`)
- ✅ Comprimento de linha: 80 caracteres
- ✅ Plugin Tailwind CSS habilitado (`prettier-plugin-tailwindcss`)
- ✅ Ordenação de imports com `importOrder`
- ✅ Separação automática de grupos de imports

### 2. **ESLint** `eslint.config.js`
- ✅ Configuração flat (novo padrão)
- ✅ Integração com TypeScript (`typescript-eslint`)
- ✅ Plugin `unused-imports` para remover imports não utilizados
- ✅ Plugin `react-refresh` para React
- ✅ Plugin `react-hooks` para regras de hooks
- ✅ Integração com Prettier (sem conflitos)
- ✅ Arquivos ignorados configurados no `globalIgnores`

### 3. **VSCode** `.vscode/settings.json`
- ✅ Auto-formatação ao salvar (`editor.formatOnSave: true`)
- ✅ Prettier como formatador padrão
- ✅ Formatação ao colar (`editor.formatOnPaste: true`)
- ✅ Espaçamento de **2 tabs** (`editor.tabSize: 2`)
- ✅ Configuração específica para `typescript`, `typescriptreact`, `javascript`, `javascriptreact`
- ✅ Régua em 80 caracteres para referência visual

### 4. **Vite** `vite.config.ts`
- ✅ Alias `@/` para a pasta `src` já configurado
- ✅ Plugin React habilitado
- ✅ Plugin Tailwind CSS habilitado

### 5. **TypeScript** `tsconfig.app.json`
- ✅ Path alias `@/*` mapeado para `src/*`
- ✅ `noUnusedLocals: true` - detecta variáveis não usadas
- ✅ `noUnusedParameters: true` - detecta parâmetros não usados

### 6. **Package.json** - Scripts adicionados
```json
{
  "lint": "eslint .",
  "lint:fix": "eslint . --fix",
  "format": "prettier --write .",
  "format:check": "prettier --check ."
}
```

---

## 🔧 Como Usar

### **Auto-formatação ao Salvar**
Sempre que você salvar um arquivo TypeScript/React, ele será automaticamente:
1. ✨ Formatado pelo Prettier
2. 🔄 Imports ordenados automaticamente
3. 🗑️ Imports não utilizados removidos
4. 🎨 Classes Tailwind reorganizadas

### **Comandos Úteis**

Executar ESLint e corrigir automaticamente:
```bash
npm run lint:fix
```

Formatar todos os arquivos:
```bash
npm run format
```

Verificar formatação sem fazer alterações:
```bash
npm run format:check
```

Validar lint sem corrigir:
```bash
npm run lint
```

---

## 📁 Estrutura de Imports Esperada

Após a configuração, seus imports serão ordenados automaticamente nesta ordem:

1. **Imports do React e bibliotecas principais**
```typescript
import React from 'react'
import { useState } from 'react'
```

2. **Imports de bibliotecas externas**
```typescript
import { useRouter } from 'react-router-dom'
import { format } from 'date-fns'
```

3. **Imports de alias e projeto**
```typescript
import { Button } from '@/components/Button'
import { useAuth } from '@/hooks/useAuth'
```

4. **Imports relativos**
```typescript
import { helper } from './utils'
import styles from './Component.module.css'
```

---

## 🎯 Regras de Lint Importantes

### ❌ Imports não utilizados
```typescript
import { unused } from '@/utils' // ❌ Erro: nunca é usado
```

### ❌ Variáveis não utilizadas
```typescript
const notUsed = 42 // ❌ Warning: nunca é usada
```

### ✅ Prefixo underscore para ignorar
```typescript
const _notUsed = 42 // ✅ OK: prefixo _ significa que é intencional
```

### ✅ Argumentos ignorados com underscore
```typescript
const callback = (_event, value) => {
  // ✅ OK: _event não é usado e está prefixado
  return value
}
```

---

## 🚀 Extensões VSCode Recomendadas

Certifique-se de ter as extensões instaladas:

1. **Prettier - Code formatter** (`esbenp.prettier-vscode`)
2. **ESLint** (`dbaeumer.vscode-eslint`)
3. **Tailwind CSS IntelliSense** (`bradlc.vscode-tailwindcss`)

Todas estão listadas em `.vscode/extensions.json`

---

## 📝 Notas Importantes

- **Formatação automática**: Habilitada ao salvar
- **Verificação de lint**: Execute `npm run lint` antes de fazer commits
- **Conflitos resolvidos**: ESLint + Prettier estão configurados para não conflitar
- **Imports organizados**: Acontece automaticamente via Prettier
- **Alias @/**: Use sempre que possível em vez de paths relativos

---

## 🔄 Próximas Etapas (Opcional)

Se desejar adicionar mais automação:

1. **Husky** + **Lint-staged** para validar antes de commits
2. **Pre-commit hooks** para garantir qualidade
3. **CI/CD** com GitHub Actions para verificação automática

Exemplo de configuração futura:
```bash
npm install -D husky lint-staged
npx husky install
```

---

**Configuração realizada em:** 2026-07-17
**Versões:**
- Prettier: ^3.5.0
- ESLint: ^10.6.0
- TypeScript: ~6.0.2
- React: ^19.2.7
