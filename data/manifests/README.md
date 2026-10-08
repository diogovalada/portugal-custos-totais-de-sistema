# Manifests de dados

Cada aquisição preservada e usada num resultado deve ter um manifest, gerado automaticamente tanto quanto possível, com pelo menos:

```yaml
source_id:
retrieved_at:
valid_at:
url_or_endpoint:
request_parameters:
license:
redistribution:
timezone:
units:
coverage:
provisional_or_final:
sha256:
acquisition_script:
transformation_commit:
notes:
```

Downloads descartáveis usados apenas para explorar uma API não exigem este formulário completo. Se forem promovidos a input, o manifest passa a ser obrigatório antes de qualquer resultado claim-bearing.
